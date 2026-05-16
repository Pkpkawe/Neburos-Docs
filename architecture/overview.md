# ARCH-001: Neburos

**Status:** draft
**Versão:** 1.0  
**Última atualização:** 16/05/2026
**Autor:** @Pkpkawe

---

## Visão Geral

A arquitetura do Neburos foi projetada para atender aos objetivos do sistema de gestão financeira pessoal, priorizando modularidade, escalabilidade, segurança e facilidade de manutenção.

Sua estrutura busca permitir a evolução gradual do projeto sem gerar alto acoplamento entre componentes, facilitando organização, expansão de funcionalidades e colaboração entre desenvolvedores.

A arquitetura também foi planejada para garantir separação clara de responsabilidades entre frontend, infraestrutura e backend, permitindo maior controle operacional e melhor capacidade de evolução futura do sistema.

## Estilo Arquitetural

O Neburos utiliza uma arquitetura baseada em:

- **Cliente-Servidor:** Separação clara entre a interface do usuário (cliente) e as regras de negócio (servidor).
- **API Gateway:** Ponto único de entrada para gerenciamento, segurança e roteamento de todas as requisições externas.
- **Estilo Arquitetural REST:** Comunicação padronizada baseada em recursos HTTP para integração entre componentes. 
- **Estrutura Modular em Camadas:** Organização interna do código dividida em responsabilidades lógicas independentes e bem definidas.
- **Estratégias de Cache:** Arquitetura otimizada para alta performance e redução de latência no acesso aos dados.
- **Monólito Modular Multirepo:** Código estruturado de forma unificada e coesa, mas distribuído organizacionalmente em múltiplos repositórios.


## Estrutura Geral do Sistema

![Neburos - C2 - C4 Model](./diagrams/Neburos%20-%20C2%20-%20C4%20Model.png)

## Componentes

| Componente | Responsabilidade | Entrada | Saída | Tecnologia |
| --- | --- | --- | --- | --- |
| Web App | Responsável pela interface gráfica do sistema e pela experiência do usuário. Realiza renderização das páginas, gerenciamento de estado da aplicação, consumo da API, validações iniciais de dados, autenticação do usuário e exibição de relatórios financeiros. Atua como camada de apresentação do sistema. | Interações do usuário, formulários, ações da interface e respostas da API | Requisições HTTP/HTTPS para o API Gateway e renderização visual das informações | React |
| API Gateway | Atua como ponto central de entrada e tráfego do sistema. Responsável pelo roteamento de requisições, proxy reverso, controle de acesso, autenticação, rate limiting, políticas de segurança, CORS, observabilidade, logs e gerenciamento centralizado das APIs. Também reduz exposição direta dos serviços internos. | Requisições HTTP/HTTPS vindas do frontend ou clientes externos | Requisições encaminhadas para a API backend e respostas retornadas ao cliente | Kong |
| API Core | Responsável pelo processamento das regras de negócio da aplicação. Executa operações CRUD, validações de domínio, autenticação, autorização, cálculos financeiros, gerenciamento de contas, categorias, metas e transações. Centraliza a lógica principal do sistema e integra os demais serviços internos. | Requisições encaminhadas pelo API Gateway | Respostas JSON, operações em banco de dados e integração com cache | FastAPI |
| Banco de Dados | Responsável pela persistência e gerenciamento das informações do sistema. Armazena usuários, contas financeiras, receitas, despesas, categorias, metas, sessões e demais dados necessários para funcionamento da aplicação. Garante integridade, consistência e relacionamento entre os dados. | Dados processados pela API backend | Dados persistidos, consultas e resultados relacionais | PostgreSQL |
| Cache | Responsável pelo armazenamento temporário de dados frequentemente acessados para redução de latência e melhoria de performance. Pode ser utilizado para cache de consultas, sessões, tokens, rate limiting e otimização de operações repetitivas. | Dados processados pela API backend | Dados em memória de alta velocidade | Redis |

## Fluxo Geral

O funcionamento geral do Neburos ocorre através da comunicação entre frontend, API Gateway, backend, cache e banco de dados.

O fluxo foi projetado para garantir:

- separação de responsabilidades;
- segurança centralizada;
- baixo acoplamento;
- escalabilidade;
- otimização de performance;
- organização do processamento interno.

### Fluxo principal da aplicação

1. O usuário acessa a interface web do Neburos através do frontend React;

2. O frontend realiza validações iniciais da interface, coleta os dados informados pelo usuário e envia requisições HTTP/HTTPS para o API Gateway;

3. O Kong API Gateway recebe todas as requisições externas da aplicação e atua como ponto central de entrada do sistema;

4. O API Gateway aplica políticas de segurança e gerenciamento, incluindo:
   - autenticação;
   - autorização;
   - rate limiting;
   - controle de CORS;
   - proxy reverso;
   - roteamento das APIs;
   - observabilidade e logs;

5. Após validação, o Kong encaminha a requisição para a API backend desenvolvida em FastAPI;

6. O backend processa a requisição executando:
   - validações de domínio;
   - regras de negócio;
   - autenticação e autorização;
   - operações CRUD;
   - cálculos financeiros;
   - gerenciamento de contas, categorias, metas e transações;

7. Durante o processamento, a API pode consultar o Redis para:
   - recuperação de dados em cache;
   - armazenamento temporário;
   - gerenciamento de sessões;
   - otimização de consultas frequentes;
   - redução de latência;

8. Caso necessário, o backend realiza operações no PostgreSQL para:
   - persistência de dados;
   - atualização de registros;
   - consultas relacionais;
   - integridade das informações financeiras;

9. O PostgreSQL retorna os dados processados para a API backend;

10. O backend estrutura a resposta em formato JSON;

11. A resposta retorna ao Kong API Gateway;

12. O API Gateway encaminha a resposta final ao frontend React;

13. O frontend processa os dados recebidos e atualiza a interface para o usuário.


<!-- ## ADRs Relacionadas -->

<!--
Liste as ADRs relacionadas a esta arquitetura.

Para cada ADR, informe:
- Identificador;
- Título da decisão;
- Breve resumo do que foi decidido.

Formato sugerido:
[ADR-001](./adr/adr-001-nome.md) — breve descrição da decisão
-->

<!-- ## Observações -->

<!-- Informações adicionais -->

## Histórico de Alterações

| Versão | Data | Alteração | Autor |
|---|---|---|---|
| 1.0 | 16/05/2026 | Criação inicial | @Pkpkawe |

<!-- ## Referências -->

<!-- Adicione links, livros, documentações e materiais usados como base. -->
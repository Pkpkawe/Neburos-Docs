# Neburos

**Software open-source de gestão financeira pessoal** desenvolvido para auxiliar usuários no controle de receitas, despesas, metas financeiras e planejamento de gastos futuros de forma simples, intuitiva e acessível.

O projeto busca fornecer uma plataforma moderna para organização financeira pessoal, permitindo maior controle sobre movimentações financeiras, categorização de transações, acompanhamento de saldo e visualização de padrões de consumo.

O Neburos é licenciado sob a GPL e foi idealizado para ser um sistema escalável, seguro e modular, seguindo boas práticas de engenharia de software e arquitetura.

## Objetivo deste Repositório

Este repositório centraliza toda a documentação oficial do projeto Neburos.

Aqui estão documentados:

- arquitetura do sistema;
- regras de negócio;
- requisitos;
- casos de uso;
- decisões arquiteturais;
- padrões técnicos;
- fluxos operacionais;
- guias de implementação;
- processos de manutenção;
- materiais de referência.

O objetivo é manter uma base de conhecimento organizada, rastreável e acessível tanto para desenvolvedores quanto para colaboradores e interessados no projeto.

## Sobre o Sistema

O Neburos permite que usuários:

- criem e gerenciem contas;
- registrem receitas e despesas;
- organizem transações por categorias;
- acompanhem saldo financeiro;
- definam metas financeiras;
- visualizem relatórios;
- acompanhem padrões de consumo;
- planejem gastos futuros.

## Arquitetura do Projeto

O sistema utiliza uma arquitetura **multirepo monolítica**, dividindo responsabilidades em múltiplos repositórios especializados sem a complexidade operacional de microsserviços distribuídos.

A estrutura do projeto é organizada em:

- frontend;
- backend;
- documentação;
- bibliotecas compartilhadas;
- infraestrutura.

Para ver mais sobre a arquitetura do projeto Neburos acesse: 

- [overview.md](./architecture/overview.md)

# Estrutura da Documentação

A documentação está organizada em módulos separados para arquitetura, negócio, requisitos, implementação e materiais auxiliares.

Para visualizar toda a estrutura detalhada da documentação, consulte o arquivo:

- [SUMMARY.md](./SUMMARY.md)

```
docs/
├── README.md
├── SUMMARY.md
├── _templates/
├── organization/ 
├── architecture/
├── business/
├── use-cases/
├── implementation/
├── requirements/
└── references/
```

## Segurança

A segurança é tratada como um dos pilares principais do projeto.

O sistema possui:

- autenticação baseada em tokens;
- criptografia de senhas;
- comunicação HTTPS;
- validações frontend/backend;
- proteção contra vulnerabilidades comuns;
- controle de permissões;
- gerenciamento seguro de sessões.

## Escalabilidade e Manutenção

A estrutura modular do Neburos foi projetada para:

- facilitar manutenção;
- permitir crescimento gradual;
- reduzir acoplamento;
- melhorar organização do código;
- facilitar colaboração em equipe;
- permitir futura evolução arquitetural.

## Licença

Neburos é um software open-source licenciado sob a GPL.
# Funcionalidade: Sistema de Inspeção de Salas com Critérios Personalizáveis

## Descrição
Implementar um sistema completo para realizar inspeções de salas, onde cada sala poderá ter diversos critérios de avaliação cadastráveis. Os critérios serão relacionados a cada sala específica e terão pontuações que impactarão o score final da sala.

## Objetivo
Permitir a avaliação sistemática de salas com base em critérios personalizáveis, gerando um score final que representa a qualidade geral da sala (nota máxima 100).

## Requisitos Funcionais

### Cadastro de Salas
- Criar interface para cadastro de salas
- Permitir edição e exclusão de salas
- Armazenar informações básicas da sala (nome, localização, capacidade, etc.)

### Cadastro de Critérios de Avaliação
- Permitir a criação de critérios de avaliação (ex: limpeza, iluminação, mobiliário)
- Definir peso/impacto de cada critério no score final
- Possibilitar a vinculação de critérios específicos para cada sala
- Permitir a edição e exclusão de critérios

### Sistema de Inspeção
- Criar interface para realizar inspeções
- Permitir selecionar uma sala para inspeção
- Exibir os critérios vinculados à sala selecionada
- Possibilitar a atribuição de notas para cada critério
- Calcular automaticamente o score final com base nas notas e pesos dos critérios
- Armazenar histórico de inspeções realizadas

### Relatórios e Visualização
- Exibir histórico de inspeções por sala
- Gerar relatórios de performance das salas ao longo do tempo
- Visualizar ranking de salas com base nos scores

## Responsabilidades

### Client (Frontend)
- Desenvolver interfaces de usuário para:
  - Cadastro e gerenciamento de salas
  - Cadastro e gerenciamento de critérios de avaliação
  - Vinculação de critérios às salas
  - Realização de inspeções
  - Visualização de resultados e relatórios
- Implementar validações de formulários
- Criar componentes reutilizáveis para os diferentes tipos de critérios
- Desenvolver visualizações gráficas para os scores e históricos
- Implementar sistema de notificação para inspeções pendentes ou com baixo score

### Server (Backend)
- Criar schema GraphQL para:
  - Salas
  - Critérios de avaliação
  - Relacionamento entre salas e critérios
  - Inspeções e seus resultados
- Implementar resolvers para todas as operações CRUD
- Desenvolver lógica para:
  - Cálculo de scores com base nos pesos dos critérios
  - Validação de regras de negócio
  - Armazenamento e recuperação eficiente dos dados
- Criar migrations para o banco de dados PostgreSQL
- Implementar testes unitários para validar a lógica de negócio

## Modelo de Dados (Sugestão Inicial)

### Salas
- id (PK)
- nome
- localizacao
- capacidade
- descricao
- data_criacao
- data_atualizacao

### Critérios
- id (PK)
- nome
- descricao
- peso (impacto no score final)
- data_criacao
- data_atualizacao

### Relacionamento Sala-Critério
- id (PK)
- sala_id (FK)
- criterio_id (FK)
- ativo (boolean)
- data_criacao
- data_atualizacao

### Inspeções
- id (PK)
- sala_id (FK)
- data_inspecao
- responsavel
- score_final
- observacoes
- data_criacao
- data_atualizacao

### Resultados de Critérios
- id (PK)
- inspecao_id (FK)
- criterio_id (FK)
- nota
- observacao
- data_criacao
- data_atualizacao

## Critérios de Aceitação
- Deve ser possível cadastrar salas com informações básicas
- Deve ser possível criar critérios de avaliação com pesos personalizáveis
- Deve ser possível vincular critérios específicos a cada sala
- O sistema deve calcular corretamente o score final com base nas notas e pesos dos critérios
- A interface deve ser responsiva e seguir os padrões de design do Quasar Framework
- O sistema deve validar entradas do usuário e fornecer feedback adequado
- As operações de banco de dados devem ser otimizadas para performance
- O código deve seguir as boas práticas e padrões do projeto

## Estimativa de Complexidade
Média-Alta

# Projeto: Esquema Conceitual de Oficina Mecânica

## Descrição

Este projeto foi desenvolvido como parte de um desafio da plataforma Digital Innovation One (DIO), com o objetivo de criar um **esquema conceitual** (Diagrama Entidade-Relacionamento) para um sistema de controle e gerenciamento de ordens de serviço em uma oficina mecânica.

O modelo conceitual representa de forma clara as entidades envolvidas no processo da oficina, seus atributos e os relacionamentos entre elas.

---

## Contexto do Desafio

A narrativa fornecida para o desafio descreve o seguinte cenário:

- Clientes levam veículos à oficina para conserto ou revisão periódica.
- Cada veículo é atendido por uma equipe de mecânicos.
- A equipe identifica os serviços a serem executados e preenche uma **Ordem de Serviço (OS)** com data de entrega.
- O valor da OS é composto por:
  - Valor da mão de obra dos serviços executados (baseado em uma tabela de referência).
  - Valor das peças utilizadas.
- O cliente autoriza a execução dos serviços.
- A mesma equipe realiza os serviços.
- Os mecânicos possuem:
  - Código, nome, endereço e especialidade.
- Cada OS possui:
  - Número (ID), data de emissão, valor total, status e data de conclusão.

---

## Entidades e Relacionamentos

### 🔹 Cliente
- `id_cliente` (PK)
- `nome`
- `telefone`
- `endereço`

### 🔹 Veículo
- `id_veiculo` (PK)
- `placa`
- `modelo`
- `ano`
- `id_cliente` (FK)

### 🔹 Mecânico
- `id_mecanico` (PK)
- `nome`
- `endereço`
- `especialidade`

### 🔹 Equipe
- `id_equipe` (PK)
- `nome_equipe`
- **Relacionamento com mecânicos (equipe_mecanico)**

### 🔹 Ordem de Serviço (OS)
- `id_os` (PK)
- `data_emissao`
- `data_conclusao`
- `valor_total`
- `status`
- `id_veiculo` (FK)
- `id_equipe` (FK)

### 🔹 Serviço
- `id_servico` (PK)
- `descricao`
- `valor_mao_obra`

### 🔹 Peça
- `id_peca` (PK)
- `nome`
- `valor_unitario`

### 🔹 OS_Serviço (Relacionamento entre OS e Serviço)
- `id_os` (FK)
- `id_servico` (FK)
- `quantidade`

### 🔹 OS_Peça (Relacionamento entre OS e Peça)
- `id_os` (FK)
- `id_peca` (FK)
- `quantidade`

### 🔹 Equipe_Mecânico (Relacionamento entre Equipe e Mecânico)
- `id_equipe` (FK)
- `id_mecanico` (FK)

---

## Diagrama Entidade-Relacionamento

📌 *Adicione aqui a imagem do seu diagrama ER ou um link para visualização online (como do Draw.io ou Lucidchart).*

---

## Observações e Suposições

- O relacionamento entre equipe e mecânicos é considerado **muitos para muitos**, permitindo flexibilidade na composição das equipes.
- Cada veículo pertence a **um cliente**.
- Cada OS pode conter **vários serviços e várias peças**.
- A tabela de valores de mão-de-obra está representada diretamente no atributo `valor_mao_obra` da entidade Serviço.
- A entidade **Equipe** centraliza os mecânicos responsáveis por uma OS, conforme descrito na narrativa.
- Caso algum item da narrativa não tenha sido explicitamente definido, foi interpretado com base em conhecimento de modelagem e contexto de oficinas.

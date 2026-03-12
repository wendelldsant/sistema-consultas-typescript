# 🏥 Sistema de Marcação de Consultas Médicas (TypeScript)

Projeto desenvolvido utilizando **TypeScript puro**, com foco em **modelagem de domínio, tipagem forte e regras de negócio** para um sistema de marcação de consultas médicas.

Este projeto foi desenvolvido como atividade prática da disciplina, aplicando conceitos importantes de **TypeScript, organização de projeto e versionamento com Git/GitHub**.

---

# 📌 Objetivo do Projeto

Desenvolver a **modelagem e regras de negócio** de um sistema capaz de:

- Criar consultas médicas
- Confirmar consultas
- Cancelar consultas
- Listar consultas por status
- Listar consultas futuras
- Calcular faturamento das consultas realizadas
- Exibir dados formatados em português

Todo o sistema foi implementado utilizando **TypeScript puro (.ts)**, sem frameworks.

---

# 🧠 Conceitos de TypeScript Utilizados

Este projeto aplica diversos conceitos fundamentais do TypeScript:

- **Type Aliases (`type`)**
- **Interfaces (`interface`)**
- **Union Types**
- **Optional Properties (`?`)**
- **Type Annotations**
- **Strict Mode**
- **Type Inference**
- **Array Typing (`Consulta[]`)**
- **Object Spread (`...`)**

---

# 📁 Estrutura do Projeto

```
sistema-consultas-typescript
│
├── src
│   │
│   ├── types
│   │   ├── especialidade.ts
│   │   ├── paciente.ts
│   │   └── statusConsulta.ts
│   │
│   ├── interfaces
│   │   ├── medico.ts
│   │   ├── consulta.ts
│   │   └── usuarioAdmin.ts
│   │
│   └── index.ts
│
├── dist
│
└── tsconfig.json
```

---

# 🧩 Modelagem do Sistema

O sistema foi modelado utilizando **tipos e interfaces** para representar as principais entidades.

## Especialidade

Representa a área médica do profissional.

```ts
export type Especialidade = {
  id: number;
  nome: string;
  descricao?: string;
};
```

---

## Paciente

Representa o paciente que realizará a consulta.

```ts
export type Paciente = {
  id: number;
  nome: string;
  cpf: string;
  email: string;
  telefone?: string;
};
```

---

## Status da Consulta

Utiliza **Union Types** para restringir valores possíveis.

```ts
export type StatusConsulta =
  | "agendada"
  | "confirmada"
  | "cancelada"
  | "realizada";
```

---

## Médico

Representa o profissional responsável pela consulta.

```ts
export interface Medico {
  id: number;
  nome: string;
  crm: string;
  especialidade: Especialidade;
  ativo: boolean;
}
```

---

## Consulta

Entidade central do sistema.

```ts
export interface Consulta {
  id: number;
  medico: Medico;
  paciente: Paciente;
  data: Date;
  valor: number;
  status: StatusConsulta;
  observacoes?: string;
}
```

---

## Usuário Administrador

Usuário responsável pela gestão do sistema.

```ts
export interface UsuarioAdmin {
  id: number;
  nome: string;
  email: string;
  nivelAcesso: "total" | "operacional" | "financeiro";
}
```

---

# ⚙️ Funcionalidades Implementadas

## Criar Consulta

Função responsável por criar uma nova consulta com status inicial **"agendada"**.

```ts
function criarConsulta(
  id: number,
  medico: Medico,
  paciente: Paciente,
  data: Date,
  valor: number
): Consulta
```

---

## Confirmar Consulta

Altera o status da consulta para **confirmada**.

```ts
function confirmarConsulta(consulta: Consulta): Consulta
```

---

## Cancelar Consulta

Cancela uma consulta, exceto se ela já estiver **realizada**.

```ts
function cancelarConsulta(consulta: Consulta): Consulta | null
```

---

## Exibir Consulta

Formata e exibe os dados da consulta de forma legível.

```ts
function exibirConsulta(consulta: Consulta): string
```

---

# 📊 Atividades Implementadas

## 1️⃣ Listar Consultas por Status

Retorna todas as consultas com determinado status.

```ts
function listarConsultasPorStatus(
  consultas: Consulta[],
  status: StatusConsulta
): Consulta[]
```

---

## 2️⃣ Listar Consultas Futuras

Filtra consultas com data maior ou igual à data atual.

```ts
function listarConsultasFuturas(consultas: Consulta[]): Consulta[]
```

---

## 3️⃣ Array Tipado de Consultas

Uso de **array tipado** para armazenar consultas.

```ts
const consultas: Consulta[] = [];
```

Consultas são criadas utilizando a função:

```ts
criarConsulta(...)
```

---

## 4️⃣ Cálculo de Faturamento

Soma os valores de consultas com status **realizada**.

```ts
function calcularFaturamento(consultas: Consulta[]): number
```

---

# ▶️ Como Executar o Projeto

## 1️⃣ Clonar o Repositório

```bash
git clone https://github.com/SEU-USUARIO/sistema-consultas-typescript.git
```

---

## 2️⃣ Entrar na Pasta

```bash
cd sistema-consultas-typescript
```

---

## 3️⃣ Compilar o Projeto

```bash
tsc
```

---

## 4️⃣ Verificar erros sem gerar arquivos

```bash
tsc --noEmit
```

---

## 5️⃣ Executar o Projeto

```bash
node dist/index.js
```

---

# 🧾 Regras do Projeto

- Não utilizar `any`
- Manter **Strict Mode ativado**
- Utilizar **type e interface corretamente**
- Não deixar **erros de compilação**
- Seguir a **estrutura de pastas definida**
- Utilizar **TypeScript puro**
- Versionamento utilizando **Git e GitHub**

---

# 💻 Tecnologias Utilizadas

- TypeScript
- Node.js
- Git
- GitHub
- VS Code

---

# 👨‍💻 Autor

Projeto desenvolvido para atividade acadêmica utilizando **TypeScript**.

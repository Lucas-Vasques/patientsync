Cole exatamente este conteúdo em `docs/api/contrato-api.md`. Apenas organizei e corrigi a formatação das decisões que você já tomou.

```markdown
# Contrato Inicial da API REST — PatientSync

## Recursos

A API REST do PatientSync disponibilizará os seguintes recursos:

- Pacientes
- Agendamentos

## Autenticação

A API será protegida e exigirá autenticação por token.

---

## Pacientes

### Endpoints

| Ação | Método | Endpoint |
|---|---|---|
| Listar pacientes | GET | `/api/pacientes/` |
| Consultar um paciente | GET | `/api/pacientes/{id}/` |
| Criar paciente | POST | `/api/pacientes/` |
| Alterar paciente | PUT/PATCH | `/api/pacientes/{id}/` |
| Remover paciente | DELETE | `/api/pacientes/{id}/` |

### Parâmetros de consulta

Buscar pacientes por nome:

```text
GET /api/pacientes/?nome=João
```

### Exemplo de requisição

```http
POST /api/pacientes/
```

```json
{
  "nome": "João Pedro",
  "numero_contato": "(61) 99999-0000"
}
```

### Exemplo de resposta

```json
{
  "id": 1,
  "nome": "João Pedro",
  "numero_contato": "(61) 99999-0000"
}
```

---

## Agendamentos

### Endpoints

| Ação | Método | Endpoint |
|---|---|---|
| Listar agendamentos | GET | `/api/agendamentos/` |
| Consultar um agendamento | GET | `/api/agendamentos/{id}/` |
| Criar agendamento | POST | `/api/agendamentos/` |
| Alterar agendamento | PUT/PATCH | `/api/agendamentos/{id}/` |
| Remover agendamento | DELETE | `/api/agendamentos/{id}/` |

### Parâmetros de consulta

Buscar agendamentos por paciente:

```text
GET /api/agendamentos/?paciente_id=1
```

Filtrar agendamentos por data:

```text
GET /api/agendamentos/?data=2026-11-16
```

### Exemplo de requisição

```http
POST /api/agendamentos/
```

```json
{
  "paciente_id": 1,
  "data": "16/11/2026",
  "horario": "16:00",
  "motivo": "Entrega da devolutiva",
  "status": "agendado"
}
```

### Exemplo de resposta

```json
{
  "id": 1,
  "paciente_id": 1,
  "data": "16/11/2026",
  "horario": "16:00",
  "motivo": "Entrega da devolutiva",
  "status": "agendado"
}
```

---

## Códigos de Status HTTP

| Situação | Código |
|---|---:|
| Consulta bem-sucedida | `200` |
| Criação bem-sucedida | `201` |
| Alteração bem-sucedida | `200` |
| Remoção bem-sucedida | `200` |
| Dados inválidos | `400` |
| Registro não encontrado | `404` |
```

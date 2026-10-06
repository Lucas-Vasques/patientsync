# Casos de Uso — PatientSync

## UC01 — Registrar agendamento

**Ator:** Profissional/Assistente  
**Objetivo:** Registrar horário, paciente e motivo da consulta.  
**Pré-condições:** O horário disponível deve ter sido definido entre o paciente e o profissional.  
**Pós-condições:** O agendamento deve estar registrado no PatientSync e no Apple Calendar.

### Fluxo principal

1. O profissional define, junto ao paciente, um horário disponível.
2. O profissional registra o horário, o motivo e o paciente no web app.
3. O PatientSync registra o agendamento no Apple Calendar.

### Fluxos alternativos

1. Caso seja necessário alterar algum dado, o profissional pode alterá-lo manualmente no web app.
2. O sistema atualiza novamente as informações no Apple Calendar.

### Exceções

1. Se houver algum dado obrigatório inválido, o sistema não conclui o cadastro e informa ao profissional que é necessário corrigir os dados.
2. Se o agendamento for salvo no PatientSync, mas a integração com o Apple Calendar falhar, o sistema informa a falha ao profissional sem perder o agendamento já registrado.

---

## UC02 — Cancelar consulta

**Ator:** Paciente  
**Objetivo:** Cancelar a consulta em caso de imprevisto.  
**Pré-condições:** Deve existir uma consulta agendada para o paciente.  
**Pós-condições:** O paciente recebe pelo WhatsApp a mensagem "Está bem, veremos você na próxima semana", e um aviso é enviado ao profissional sobre o cancelamento.

### Fluxo principal

1. O lembrete é enviado 24 horas antes da consulta.
2. O paciente seleciona a opção de cancelar a consulta.
3. O sistema envia a mensagem "Está bem, veremos você na próxima semana".
4. O sistema envia um aviso ao profissional informando que a consulta foi cancelada.

### Fluxos alternativos

1. Caso o paciente não selecione a opção de cancelamento, a consulta permanece agendada normalmente.

### Exceções

1. Se o envio pelo WhatsApp falhar, o sistema registra a falha e avisa o profissional/assistente no PatientSync.
2. O cancelamento não é considerado confirmado enquanto o sistema não receber a ação de cancelamento do paciente.

---

## UC03 — Consultar agendamentos

**Ator:** Profissional/Assistente  
**Objetivo:** Consultar e visualizar agendamentos.  
**Pré-condições:** Os agendamentos devem ter sido cadastrados no sistema.  
**Pós-condições:** O ator poderá visualizar e consultar os agendamentos registrados.

### Fluxo principal

1. O profissional seleciona um agendamento.
2. O profissional visualiza e consulta as informações do agendamento.

### Fluxos alternativos

1. Caso o profissional não encontre um agendamento por meio do paciente ou da data pesquisada, o sistema exibe a mensagem "Agendamento não encontrado".

### Exceções

1. Caso o sistema não consiga carregar os agendamentos cadastrados, será exibida uma mensagem informando que ocorreu um erro ao visualizar os agendamentos.

---

## UC04 — Alterar agendamento

**Ator:** Profissional/Assistente  
**Objetivo:** Alterar dados do agendamento.  
**Pré-condições:** O agendamento deve estar registrado e salvo no sistema.  
**Pós-condições:** Os dados alterados devem estar salvos no PatientSync e atualizados no Apple Calendar.

### Fluxo principal

1. O profissional seleciona o agendamento.
2. O profissional altera os dados desejados.
3. O profissional salva o agendamento.
4. O sistema atualiza o agendamento no Apple Calendar.

### Fluxos alternativos

1. Caso o profissional não consiga salvar os dados alterados, o sistema exibe uma mensagem informando que não foi possível salvar o agendamento.

### Exceções

1. Caso os dados alterados não sejam atualizados no Apple Calendar, o sistema exibe uma mensagem avisando o profissional sobre a falha.

---

## UC05 — Remover agendamento

**Ator:** Profissional/Assistente  
**Objetivo:** Remover um agendamento.  
**Pré-condições:** O agendamento deve estar registrado no sistema.  
**Pós-condições:** O agendamento deve ser removido do PatientSync e do Apple Calendar.

### Fluxo principal

1. O profissional seleciona o agendamento.
2. O profissional seleciona a opção de remover o agendamento.
3. O sistema remove o agendamento e atualiza o Apple Calendar.

### Fluxos alternativos

1. Caso o profissional desista da remoção antes de confirmá-la, o sistema cancela a operação e mantém o agendamento registrado.

### Exceções

1. Caso o agendamento não seja removido do Apple Calendar, o sistema exibe uma mensagem avisando o profissional sobre a falha.

---

## UC06 — Enviar lembrete de consulta

**Atores:** Paciente e serviço de WhatsApp  
**Objetivo:** Enviar um lembrete da consulta para que o paciente possa comparecer ou cancelar.  
**Pré-condições:** O agendamento já deve estar registrado no sistema.  
**Pós-condições:** O paciente recebe um lembrete sobre sua consulta 24 horas antes do horário agendado.

### Fluxo principal

1. O paciente recebe uma mensagem via WhatsApp 24 horas antes da consulta.
2. O paciente pode escolher a opção de cancelar ou não cancelar a consulta.
3. Caso o paciente não selecione a opção de cancelamento, a consulta continua agendada normalmente.

### Fluxos alternativos

1. Caso o paciente selecione a opção de cancelamento, inicia-se o UC02 — Cancelar consulta.

### Exceções

1. Caso o serviço de WhatsApp esteja indisponível ou o envio do lembrete falhe, o sistema registra a falha e avisa o profissional/assistente.
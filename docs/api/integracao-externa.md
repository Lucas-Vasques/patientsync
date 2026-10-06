# Plano de Integração Externa — PatientSync

## 1. Twilio WhatsApp API

### Finalidade

A Twilio WhatsApp API será a principal API externa utilizada pelo PatientSync.

A integração será utilizada para:

- Enviar um lembrete ao paciente 24 horas antes da consulta.
- Receber a ação de cancelamento realizada pelo paciente através do WhatsApp.

### Envio do lembrete

Quando chegar 24 horas antes da consulta, o PatientSync enviará uma mensagem para o número de WhatsApp do paciente utilizando a API da Twilio.

Endpoint utilizado para o envio:

POST https://api.twilio.com/2010-04-01/Accounts/{AccountSid}/Messages.json

O lembrete será enviado utilizando um template de mensagem aprovado para WhatsApp.

Os principais dados utilizados serão:

- Número de WhatsApp autorizado como remetente.
- Número de WhatsApp do paciente.
- Conteúdo do template de lembrete.

### Recebimento do cancelamento

Quando o paciente cancelar pelo WhatsApp, a Twilio enviará uma requisição para um webhook do PatientSync.

Webhook definido:

POST /webhooks/twilio/whatsapp/

O PatientSync utilizará os seguintes dados recebidos:

- Número do paciente.
- Identificador da mensagem.
- Conteúdo da resposta ou ação de cancelamento selecionada.

Após receber essas informações, o Django processará a requisição para confirmar o cancelamento da consulta.

### Autenticação

A comunicação do PatientSync com a API da Twilio utilizará:

- API Key SID.
- API Key Secret.

As credenciais serão armazenadas em variáveis de ambiente e não serão adicionadas ao repositório GitHub.

### Tratamento de falhas

Se a Twilio falhar ao enviar o lembrete ou processar um cancelamento, o PatientSync deverá:

- Registrar a falha.
- Avisar o profissional ou assistente dentro do PatientSync.

### Limitações

O envio das notificações depende da configuração do serviço de WhatsApp na Twilio.

Para mensagens iniciadas pelo PatientSync fora da janela de atendimento do WhatsApp, será utilizado um template de mensagem aprovado.

### Documentação oficial consultada

- Twilio — Messages Resource.
- Twilio — Messaging Webhooks.
- Twilio — Twilio API Requests.
- Twilio — WhatsApp Notification Messages with Templates.

---

## 2. Integração com Apple Calendar

### Finalidade

O PatientSync também realizará uma integração adicional com o Apple Calendar através do iCloud Calendar utilizando CalDAV.

Essa integração será utilizada para sincronizar os agendamentos registrados pelo profissional.

### Dados sincronizados

O evento registrado no Apple Calendar terá:

- Nome do paciente.
- Data.
- Horário.

### Operações

Quando o profissional registrar um agendamento, o PatientSync criará o evento no Apple Calendar.

Quando o profissional alterar um agendamento, o PatientSync atualizará o evento correspondente.

Quando o profissional remover um agendamento, o PatientSync removerá o evento correspondente do Apple Calendar.

### Autenticação

A integração utilizará uma senha específica de app da Conta Apple.

A credencial será armazenada em variável de ambiente e não será adicionada ao repositório GitHub.

### Tratamento de falhas

Se a sincronização com o Apple Calendar falhar, o PatientSync avisará o profissional sobre a falha.

### Limitações

A integração depende de:

- Uma Conta Apple configurada.
- Acesso ao iCloud Calendar.
- Comunicação através do padrão CalDAV.

O endereço específico do calendário/servidor utilizado na implementação deverá ser configurado e validado durante o desenvolvimento.

### Documentação oficial consultada

- Apple Support — Acessar Mail do iCloud, Calendário e Contatos em apps de terceiros.
- Apple Support — Senhas específicas de apps.
- Apple Support — Visão geral da segurança de dados do iCloud.
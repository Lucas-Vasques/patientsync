# Arquitetura — PatientSync

## Visão geral

O profissional preenche um agendamento por meio da interface web. Depois disso, as informações são enviadas ao backend desenvolvido em Django, que processa os dados e os registra no banco de dados SQLite.

Ao registrar, alterar ou remover um agendamento, o backend Django sincroniza as informações com o Apple Calendar. Vinte e quatro horas antes da consulta, o Django aciona o serviço de WhatsApp para enviar um lembrete ao paciente.

## Componentes e responsabilidades

### Interface Web

Demonstra visualmente as informações ao usuário e recebe suas ações.

### Backend Django

Recebe as ações realizadas pela interface, aplica a lógica do sistema, salva e consulta os dados no banco de dados e coordena as integrações com o Apple Calendar e o WhatsApp.

### Banco de Dados — SQLite

Registra e armazena os dados utilizados pelo sistema.

### Apple Calendar

Serviço externo utilizado para registrar e sincronizar os agendamentos do profissional.

### WhatsApp

Serviço externo utilizado para a comunicação com o paciente por meio dos lembretes das consultas.

## Fluxo de dados

Interface Web → Backend Django  
**Dados e ações do usuário**

Backend Django → SQLite  
**Salvar e consultar dados**

Backend Django → Apple Calendar  
**Sincronizar agendamentos**

Backend Django → WhatsApp  
**Enviar lembrete e receber cancelamento**

## Tecnologias

- Python
- Django
- SQLite

## Integrações externas

- Apple Calendar
- WhatsApp
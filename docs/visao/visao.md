# Documento de Visão — PatientSync

## Contexto e problema

Pacientes esquecem de comparecer às consultas e de cancelar os agendamentos.

## Justificativa

Devido a isso, o profissional fica com blocos vazios de tempo em sua rotina, fazendo com que perca tempo e dinheiro.

## Objetivo geral

O objetivo do PatientSync é tornar o processo de agendamento mais eficiente e reduzir os blocos vazios de tempo causados pelo esquecimento do paciente em comparecer ou cancelar a consulta.

## Objetivos específicos

- Registrar automaticamente os agendamentos no Apple Calendar após o registro realizado pelo profissional no web app.
- Enviar um lembrete ao paciente 24 horas antes da consulta, com opção de cancelamento.
- Enviar um aviso ao profissional quando uma consulta for cancelada.

## Público-alvo

Profissionais de clínica.

## Stakeholders

- Pacientes.
- Profissionais e assistentes.
- Clínica.

## Escopo

- Registro de pacientes e agendamentos pelo profissional ou assistente no web app.
- Registro automático dos agendamentos no Apple Calendar.
- Envio automático de lembretes pelo WhatsApp.
- Consulta e visualização dos agendamentos.

## Fora do escopo

- Gestão financeira completa.
- Prontuário eletrônico seguro.

## Restrições

- Python.
- Django.
- WhatsApp.
- Apple Calendar.

## Premissas

Um lembrete será suficiente para reduzir o risco de o paciente esquecer a consulta.

## Riscos

O paciente pode esquecer a consulta mesmo após receber o lembrete.

## Critérios de sucesso

A primeira versão será considerada bem-sucedida caso o sistema consiga registrar corretamente as informações dos agendamentos, permitir sua consulta e visualização, registrá-los automaticamente no Apple Calendar, enviar automaticamente o lembrete ao paciente com opção de cancelamento e avisar o profissional quando ocorrer um cancelamento.

## Funcionalidades

- Registro manual de agendamentos.
- Registro automático dos agendamentos no Apple Calendar.
- Envio automático de lembrete 24 horas antes da consulta, com opção de cancelamento.
- Aviso de cancelamento ao profissional.
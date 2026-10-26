# 🎯 Desafio Criativo: Planejando Automações com N8N Usando Apenas Bons Prompts

> Atividade prática de Engenharia de Prompt para planejamento de workflows e automações no N8N — Desenvolvido para o Bootcamp da **DIO (Digital Innovation One)**.

---

## 🧱 Passo 1: Definição da Automação Desejada

**Processo:**  
Quero criar uma automação no N8N para triagem e resposta automática de dúvidas de clientes recebidas por e-mail.

**Público ou responsável:**  
Equipe de Suporte e Atendimento ao Cliente.

**Resultado esperado:**  
Classificar a urgência do e-mail usando IA, salvar o chamado em uma base de dados e enviar uma resposta automática com orientações iniciais ao cliente.

---

## 🧱 Passo 2: Contexto, Ferramentas e Regras

**Ferramentas envolvidas:**  
- **Gmail:** Gatilho para monitoramento de novos e-mails.
- **OpenAI / Gemini:** Inteligência Artificial para análise semântica, urgência e sentimento.
- **Google Sheets:** Banco de dados para registro histórico dos chamados.
- **Slack / Telegram:** Canal de comunicação interna para alertas urgentes.

**Fluxo desejado:**  
1. Receber um novo e-mail na caixa de suporte.
2. Analisar o sentimento e o nível de urgência da mensagem com IA.
3. Gravar o log do atendimento na planilha com data, remetente e classificação.
4. Enviar um e-mail de confirmação ao cliente com tempo estimado de resposta.
5. Se a urgência for ALTA, enviar um alerta imediato no canal de comunicação da equipe de plantão.

**Regras importantes:**  
- Ignorar mensagens marcadas como spam ou e-mails sem corpo de texto.
- Se houver anexos na mensagem, armazenar a referência/link no registro da planilha.
- Disparar a notificação crítica no Slack apenas se o status retornado pela IA for `ALTA`.

---

## 🧱 Passo 3: Prompt Final Estruturado

Abaixo está o prompt consolidado, estruturado para orientar um modelo de IA a gerar a especificação exata do fluxo no N8N:

```text
Atue como um especialista sênior em automações com N8N.

Crie uma automação completa para triagem e resposta automática de dúvidas de clientes recebidas por e-mail.

Público:
Equipe de Suporte e Atendimento ao Cliente.

Ferramentas envolvidas:
Gmail (Trigger), OpenAI/Gemini (Node de IA), Google Sheets e Slack.

Fluxo desejado:
1. Receber novo e-mail pelo trigger do Gmail;
2. Analisar o corpo da mensagem com IA para extrair: categoria da dúvida, sentimento e nível de urgência (BAIXA, MEDIA, ALTA);
3. Salvar os dados categorizados em uma nova linha no Google Sheets;
4. Enviar e-mail de resposta automática personalizada ao cliente informando o recebimento;
5. Caso o nível de urgência seja ALTA, enviar uma notificação imediata no canal #urgencias-suporte do Slack.

Regras:
- Ignorar e-mails sem texto ou identificados como spam;
- Garantir tratamento de erro caso a API da IA falhe;
- Somente notificar o Slack para casos com urgência ALTA.

Explique passo a passo quais nós do N8N devem ser utilizados, a lógica das conexões condicionais (IF/Switch) e apresente o JSON base do workflow para importação.

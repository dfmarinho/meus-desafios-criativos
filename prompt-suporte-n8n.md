# Atue como um especialista em N8N

Crie uma automação para fazer a triagem automática, análise de sentimento, roteamento inteligente e registro de mensagens de suporte recebidas via WhatsApp usando Inteligência Artificial.

## Público
Equipe de suporte ao cliente e gestores de atendimento.

## Ferramentas envolvidas
- WhatsApp API (ex: Evolution API / Z-API)
- OpenAI (ChatGPT)
- Google Sheets ou Notion
- Slack (Canal de plantão)

## Fluxo
1. **Gatilho (Webhook):** O n8n recebe a mensagem enviada pelo cliente via WhatsApp em tempo real.
2. **Processamento com IA:** O texto da mensagem é enviado para a OpenAI, que classifica a urgência (Alta, Média, Baixa), o sentimento (Positivo, Neutro, Negativo) e gera um resumo do problema.
3. **Decisão (If/Switch):** O fluxo avalia o nível de urgência retornado pela IA.
4. **Notificação e Registro:** Se a urgência for Alta, dispara um alerta com menção no Slack; em seguida, salva todos os dados estruturados em uma linha do Google Sheets/Notion.

## Regras
- **Filtro anti-loop:** Ignorar mensagens enviadas pela própria empresa (mensagens de eco) ou arquivos de mídia/áudio por enquanto, focando apenas em texto.
- **Resiliência:** Em caso de falha na API da OpenAI, o fluxo deve redirecionar a mensagem para uma fila de fallback sem quebrar a execução.
- **Padronização:** Garantir que o número de telefone do cliente esteja limpo e formatado corretamente antes de salvar no banco de dados.

---

*Explique quais nós do N8N devem ser utilizados e a lógica de funcionamento do workflow.*
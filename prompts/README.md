# prompts/

Registro do que foi pedido à IA, a qual modelo e em que ferramenta.

Um arquivo por interação relevante, nomeado `NN-descricao-curta.md`. "Relevante"
significa que mudou o código, mudou a especificação ou mudou o seu entendimento do
problema. Conversa de tira-dúvidas não precisa entrar.

Este registro atende à exigência do plano de ensino de manter "registros essenciais das
interações com a IA" e de declarar o uso de IA. Como fica versionado no Git, cada
registro carrega data e autoria automáticas.

## Modelo de ficha

Copie o bloco abaixo para o seu arquivo.

```markdown
# NN — título curto do que foi pedido

- **Data:** AAAA-MM-DD
- **Autoria:** seu nome
- **Ferramenta:** Codex CLI / Claude Code / OpenCode / Antigravity / navegador
- **Modelo:** nome e versão, se souber
- **Trilha:** local / nuvem / navegador
- **Requisito ou critério alvo:** RF-0X / CA-0X

## O que foi pedido

Cole o prompt como foi enviado. Não reescreva depois para ficar melhor —
o valor do registro está em ser fiel.

## Contexto fornecido

O que a ferramenta tinha à disposição: arquivos abertos, AGENTS.md,
trechos colados, resultado de testes anteriores.

## O que veio

Resumo do que o modelo produziu. O código em si fica no commit, não aqui.

## O que eu fiz com isso

Aceitei como veio / corrigi o quê / descartei por quê.
```

## Uma observação sobre honestidade

O registro tem valor se for verdadeiro. Prompt reescrito depois para parecer mais
inteligente, ou tentativa fracassada apagada do histórico, retira do registro
exatamente aquilo que o torna útil — para você e para a avaliação. Tentativa que deu
errado costuma ensinar mais que a que deu certo, e vale nota igual.

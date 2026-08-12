# evidencias/

Registro do que aconteceu quando o código foi executado: resultado dos testes, tempo,
consumo e retrabalho.

Enquanto `prompts/` guarda a intenção, aqui fica o efeito. Um arquivo por sessão de
trabalho, nomeado `AAAA-MM-DD-descricao.md`.

## Modelo de ficha

```markdown
# AAAA-MM-DD — título da sessão

- **Autoria:** seu nome
- **Ferramenta e modelo:** 
- **Trilha:** local / nuvem / navegador
- **Ambiente:** sistema operacional, RAM, se rodou modelo local

## Ponto de partida

Quantos testes passavam antes de começar.

## Resultado

Saída de `uv run pytest`, resumida ou colada. Quantos passaram, quais falharam.

| Métrica | Valor |
|---|---|
| Testes passando antes | |
| Testes passando depois | |
| Tempo total da sessão | |
| Rodadas até passar | |
| Correções manuais necessárias | |

## O que precisou de retrabalho

Onde o modelo errou e o que você teve de consertar à mão. Esta seção é a mais
importante do arquivo — é dela que sai a análise crítica do experimento comparativo.

## O que eu entendi do código

Explique com suas palavras o que a solução faz. Se não conseguir explicar, o código
ainda não é seu — e a defesa técnica individual vai cobrar isso.
```

## Sobre segredos

Antes de colar saída de terminal, confira se não vai junto nenhum token, chave de API
ou caminho com dado pessoal. Uma vez no histórico do Git, remover dá trabalho.

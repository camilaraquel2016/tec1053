# AGENTS.md

Instruções persistentes para agentes de programação que trabalharem neste repositório.

Este arquivo segue o formato aberto descrito em <https://agents.md/>. Ele é lido por
Codex, Claude Code, OpenCode, Antigravity e outras ferramentas — a mesma instrução vale
para todas. Essa neutralidade é intencional e faz parte do conteúdo da disciplina: o
contexto pertence ao repositório, não à ferramenta.

## O que é este projeto

Repositório-base da disciplina TEC.1053 — Tópicos Especiais em Programação (IFPI,
Tecnologia em ADS). Implementa um validador de senha usado como objeto comum de estudo:
todas as pessoas da turma resolvem o mesmo problema, com a mesma especificação e os
mesmos testes, variando o modelo e a ferramenta.

## Fonte de verdade

`ESPECIFICACAO.md` é normativo. Em qualquer divergência entre a especificação, o
código existente e o que parecer razoável, **a especificação vence**.

Leia a especificação inteira antes de alterar `src/`. A seção 4 redefine o que conta
como maiúscula, minúscula, dígito, caractere especial e espaço em branco. Essas
definições **não** coincidem com o comportamento padrão dos métodos de `str` do Python.

## Comandos

```bash
uv run pytest              # roda a suíte completa
uv run pytest -x           # para no primeiro erro
uv run ruff check .        # análise estática
uv run ruff format .       # formatação
```

Não é preciso criar ambiente virtual nem instalar Python: o `uv` resolve a partir de
`.python-version` e `uv.lock`.

## Regras para o agente

**Não altere os testes.** `tests/` é o árbitro comum do experimento comparativo. Uma
solução que passa porque o teste foi afrouxado não resolveu o problema. Se você tem
motivo para crer que um teste contradiz `ESPECIFICACAO.md`, relate a contradição em vez
de editar o teste.

**Não altere o contrato.** A dataclass `ResultadoValidacao` e a assinatura de
`validar_senha` são parte da especificação.

**Não amplie o escopo.** A seção 7 lista o que está fora: entropia, verificação de
vazamentos, hashing, internacionalização, interface. Não adicione dependências —
o projeto resolve com a biblioteca padrão.

**Não invente requisitos.** Se a especificação é omissa sobre um caso, diga que é
omissa. Não preencha a lacuna silenciosamente com uma suposição.

**Faça incrementos pequenos.** Uma mudança coerente por vez, com os testes rodando
entre elas.

## Registro do trabalho

Este repositório avalia processo, não só resultado. Ao concluir uma tarefa relevante:

- registre em `prompts/` o que foi pedido, a qual modelo e em que ferramenta;
- registre em `evidencias/` o que saiu, quanto tempo levou e o que precisou de correção.

Os modelos de ficha estão em `prompts/README.md` e `evidencias/README.md`. Esse
registro alimenta três dos quatro pesos da avaliação e a declaração de uso de IA
exigida pelo plano de ensino.

## Convenções de código

- Python 3.13, tipagem nas assinaturas públicas.
- Docstrings no formato Google, em português.
- Nomes de identificadores em português, acompanhando o domínio (`validar_senha`,
  `erros`), o que é a convenção já estabelecida no código existente.
- `ruff` com as regras de `pyproject.toml` decide estilo. Não discuta formatação.

## Segurança

Nunca escreva credenciais, tokens ou chaves de API no repositório, nem em `prompts/`
ou `evidencias/`. Ao colar saída de terminal nas evidências, remova qualquer segredo
antes.

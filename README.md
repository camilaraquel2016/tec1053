# Validador de Senha — repositório-base da TEC.1053

Repositório-base da disciplina **Tópicos Especiais em Programação** (TEC.1053),
Tecnologia em Análise e Desenvolvimento de Sistemas, IFPI — Campus Teresina Central,
2026/2.

Todo mundo resolve o mesmo problema, com a mesma especificação e os mesmos testes.
O que varia é o modelo, a ferramenta e o caminho até a solução. É essa variação que
vamos comparar.

## Comece aqui

### 1. Instale o `uv`

É a única coisa que você precisa instalar. Não instale Python — o `uv` cuida disso.

**macOS e Linux:**

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows (PowerShell):**

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Feche e reabra o terminal depois de instalar.

### 2. Clone e rode os testes

```bash
git clone https://github.com/aislanifpi/tec1053-validador-senha.git
cd tec1053-validador-senha
uv run pytest
```

Na primeira execução o `uv` baixa o Python 3.13 e o pytest. Depois é instantâneo.

### 3. Veja tudo vermelho

É o esperado. A função `validar_senha` ainda não está implementada — esse é o
exercício. Cada teste que falha aponta um critério de aceitação a cumprir.

## O que fazer

1. Leia [`ESPECIFICACAO.md`](ESPECIFICACAO.md) inteiro. É o documento normativo.
2. Implemente `validar_senha` em `src/validador_senha/validador.py`.
3. Rode `uv run pytest` até tudo passar.
4. Registre o processo em [`prompts/`](prompts/) e [`evidencias/`](evidencias/).

**Não altere os testes.** Eles são o árbitro comum: se cada pessoa ajustar a régua, a
comparação entre modelos perde o sentido. Se você acha que um teste contradiz a
especificação, abra uma issue — isso conta a favor, não contra.

## Estrutura

```
ESPECIFICACAO.md   documento normativo: requisitos e critérios de aceitação
AGENTS.md          instruções persistentes para agentes de IA
src/               a implementação (é aqui que você trabalha)
tests/             a suíte de verificação (não mexa)
prompts/           registro do que foi pedido à IA
evidencias/        registro do que aconteceu ao executar
```

## Ferramentas de IA

Você pode usar qualquer ferramenta: Codex, Claude Code, OpenCode, Antigravity, Copilot,
ou o chat do navegador. Também pode não usar nenhuma. O que a disciplina exige é que
o uso seja **declarado** e **registrado**.

O arquivo `AGENTS.md` é lido automaticamente por várias dessas ferramentas e já contém
as regras do repositório. Vale abrir e ler: entender o que ele faz é conteúdo da
Unidade 3.

### Se você não tem acesso a nenhuma ferramenta paga

Você não precisa de nenhuma. Há caminhos gratuitos, e o material da disciplina traz o
passo a passo de pelo menos um deles. Modelos pequenos rodando na sua própria máquina
dão conta deste exercício.

### Se a sua máquina é fraca, ou você não tem máquina

Também há caminho. O laboratório e as rotas em navegador cobrem o exercício inteiro.
Fale comigo se o seu caso não estiver contemplado — resolvemos antes de virar problema
de nota.

## Sobre avaliação

A nota olha para **processo e evidências**, não para o tamanho do modelo nem para a
velocidade do computador. Máquina modesta não prejudica ninguém. Ferramenta paga não dá
vantagem.

O que pesa: a clareza da especificação que você produz, a rastreabilidade entre
critério e teste, a qualidade do registro, e a sua capacidade de **explicar e defender**
o código. Código que você não consegue explicar não conta como seu — vale para código
escrito por IA e para código copiado de qualquer outra fonte.

## Licença

MIT. Veja [`LICENSE`](LICENSE).

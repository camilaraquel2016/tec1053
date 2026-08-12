# Trilhas de IA

Há mais de um caminho para usar IA nesta disciplina. Todos servem, e nenhum dá vantagem
na nota. Escolha pelo que a sua situação permite.

> **Situação deste documento:** a trilha local está testada e descrita abaixo. As
> trilhas em nuvem e em navegador serão detalhadas antes da primeira atividade que as
> exija. Cotas de serviços gratuitos mudam com frequência — este documento só afirma o
> que foi conferido, e a data da conferência está sempre indicada.

## Antes de escolher: gerar e agir são coisas diferentes

Essa distinção decide o que cabe na sua máquina.

**Gerar** é pedir código e receber texto de volta. Você lê, cola, roda os testes e
corrige. O modelo não toca em nada.

**Agir** é o modelo trabalhando como agente: lendo os seus arquivos, editando código e
rodando os testes sozinho, num laço de várias etapas. Isso exige chamar ferramentas de
forma confiável, o que é bem mais difícil do que produzir texto.

Modelos pequenos geram bem. **Agir, não.** Conferido em 12/08/2026 nesta disciplina:
modelos de 3B não sustentaram o laço de agente no OpenCode — inventaram nome de
ferramenta e escreveram a chamada como texto em vez de executá-la.

Portanto: **a trilha local serve para gerar; agentes precisam de nuvem.** Não é
limitação da sua máquina, é limitação de modelo pequeno. Os laboratórios da disciplina
são de geração e verificação, então a trilha local resolve todos eles.

## Trilha local — modelo rodando na sua máquina

Zero custo, zero cadastro, funciona sem internet. É o piso garantido da disciplina.

Instale o [Ollama](https://ollama.com/download) e baixe um modelo pequeno:

```bash
ollama pull qwen2.5-coder:3b
ollama run qwen2.5-coder:3b
```

### Cabe na sua máquina?

Conferido em 12/08/2026 num MacBook Air M1 com 8 GB de RAM:

| Modelo | Disco | Tempo da primeira resposta | RAM em uso |
|---|---:|---:|---:|
| `gemma3:1b` | 815 MB | 7 s | 866 MB |
| `llama3.2:3b` | 2,0 GB | 10 s | 2,3 GB |
| `qwen2.5-coder:3b` | 1,9 GB | 15 s | 2,1 GB |

Com 8 GB de RAM, modelos de 1B a 3B rodam bem. Feche o que não estiver usando. Acima
disso, a máquina começa a usar disco como memória e tudo fica lento.

Para ver o consumo real enquanto o modelo está carregado:

```bash
ollama ps
```

Vale rodar esse comando e olhar o número. Entender que um modelo ocupa memória de
verdade, e quanto, é conteúdo da Unidade 1.

### Como trabalhar na trilha local

Converse com o modelo no terminal, peça o código, cole no arquivo e **rode os testes**:

```bash
ollama run qwen2.5-coder:3b
```

O passo de rodar os testes não é opcional nem burocracia. Numa medição feita em
12/08/2026, o `qwen2.5-coder:3b` gerou um validador de senha correto na aparência e, nos
comentários logo abaixo, errou os três exemplos de saída que ele mesmo escreveu. O código
também aceitava `"ÇÇÇÇÇÇÇ٣"` como senha válida, por usar `isupper()` e `isdigit()`, que
seguem regras Unicode.

Nada disso aparece na leitura. Tudo aparece na execução.

### O modelo local como agente

Não funciona bem com 3B, como explicado no início deste documento. Se você quiser tentar
mesmo assim, o OpenCode aceita o Ollama como provedor:

```jsonc
// ~/.config/opencode/opencode.jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "ollama": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "Ollama (local)",
      "options": { "baseURL": "http://localhost:11434/v1" },
      "models": { "llama3.2:3b": { "name": "Llama 3.2 3B (local)" } }
    }
  }
}
```

Entre os modelos testados, só o `llama3.2:3b` produziu chamadas de ferramenta bem
formadas — e ainda assim se perdeu no laço de várias etapas. O `qwen2.5-coder:3b` não
produziu nenhuma. Fica registrado como experimento, não como caminho recomendado.

## Trilha em nuvem — modelo em servidor externo

Modelos maiores, respostas mais rápidas, sem consumir a sua máquina. É a trilha
necessária para usar agentes. Em troca, os seus dados saem do equipamento e você depende
de conexão e de cota.

Há opções gratuitas. O passo a passo da que a disciplina vai adotar entra aqui antes da
primeira atividade que dependa de nuvem.

**Se você já paga por alguma ferramenta**, pode usá-la. Não gera vantagem avaliativa —
está no plano de ensino.

## Trilha em navegador — sem instalar nada

Para quem não pode instalar software no computador do laboratório, ou não tem máquina
própria. O ambiente inteiro roda no navegador, incluindo terminal e Git.

A rota escolhida entra aqui depois de testada de ponta a ponta com este repositório.

## Qual escolher

| Sua situação | Trilha |
|---|---|
| Máquina própria com 8 GB ou mais | Local |
| Máquina própria fraca, com internet boa | Nuvem |
| Só o computador do laboratório, sem permissão de instalar | Navegador |
| Sem máquina própria e sem internet em casa | Navegador, no laboratório |

Pode usar mais de uma. Aliás, **deve**: comparar o mesmo problema em trilhas diferentes
é exatamente o experimento comparativo da Unidade 5.

## Registre a trilha usada

As fichas de `prompts/` e `evidencias/` têm um campo para isso. Sem saber em que
ambiente o resultado foi produzido, não há comparação possível.

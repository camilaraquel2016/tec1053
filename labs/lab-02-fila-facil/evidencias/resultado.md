# Relatório de Evidências — Lab 02 Fila Fácil

- **Dupla**: Camila Raquel e Ariele Macêdo
- **Ferramenta**: OpenCode (Harness)
- **Modelo**: Big Pickle OpenCode Zen
- **Data**: 22/09/2026

## Evolução dos Testes (Suíte de 24 testes)
1. **Linha de base**: 6 aprovados, 18 falhas
2. **Incremento 1 (`emitirSenha`)**: 10 aprovados, 14 falhas
3. **Incremento 2 (`chamarProxima`)**: 20 aprovados, 4 falhas
4. **Incremento 3 (`reiniciarFila`)**: 24 aprovados, 0 falhas

## Verificação Visual e Funcional
- Interface testada no navegador (`http://127.0.0.1:8000/`).
- Emissão de senhas (N001, N002, N003) operando e avançando numeração.
- Chamada de senhas em ordem FIFO atualizando o painel principal.
- Fila vazia preservando o último atendimento.
- Reinício da fila sob confirmação limpando o estado e retornando a N001.

## Segurança do Contrato (Git Diff)
- O comando `git diff labs/lab-02-fila-facil/tests` retornou totalmente vazio, confirmando que a suíte de testes não foi alterada.



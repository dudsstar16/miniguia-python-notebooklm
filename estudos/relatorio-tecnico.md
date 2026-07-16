# 📊 Relatório Técnico: Fundamentos de Programação em Python

Este documento consolida os conceitos estruturais de lógica de programação aplicados ao ecossistema Python, servindo como manual de consulta rápida.

---

## 🧠 Lógica e Execução Linear
O interpretador Python lê e executa o código de forma linear (de cima para baixo, da esquerda para a direita). Por isso, a ordem de declaração de variáveis e funções é estrita.

### 📌 Tipagem Dinâmica e Fortemente Tipada
*   **Dinâmica:** Não é necessário declarar o tipo da variável ao criá-la. O interpretador infere o tipo automaticamente.
*   **Forte:** Python não realiza conversões implícitas que possam gerar perda de dados (ex: tentar somar `string` com `int` sem conversão explícita resultará em `TypeError`).

---

## 🛠️ Tratamento de Erros e Exceções (Mecanismo Try/Except)
A robustez de um software depende de como ele lida com falhas. Em Python, usamos blocos de captura para evitar o encerramento abrupto do programa.

```python
try:
    # Código que pode gerar falha
    valor = int(input("Digite um número: "))
    resultado = 10 / valor
except ZeroDivisionError:
    print("Erro: Divisão por zero não permitida.")
except ValueError:
    print("Erro: Entrada inválida. Digite apenas números.")

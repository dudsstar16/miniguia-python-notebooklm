# 🏛️ Programação Orientada a Objetos (POO) em Python

A POO é um paradigma de programação que estrutura o software mapeando elementos do mundo real em moldes de código conhecidos como **Classes** e **Objetos**.

---

## 🧩 Elementos Fundamentais da POO

![Analogia de Classes e Objetos](../imagem/analogia-poo.png)

*   **Classe (Molde):** É o projeto ou gabarito estrutural.... Define quais características e ações o elemento terá.
*   **Objeto (Instância):** É a representação física/real baseada na classe.

### 2. Atributos e Métodos
*   **Atributos (`self.atributo`):** Representam os dados ou estados de um objeto (ex: `cor`, `nome`).
*   **Métodos (`def acao(self)`):** São funções internas que determinam o comportamento do objeto.

```python
# Exemplo Prático de Implementação
class Funcionario:
    def __init__(self, nome, salario_base):
        self.nome = nome                  # Atributo
        self.salario_base = salario_base  # Atributo

    def exibir_dados(self):               # Método
        print(f"Funcionário: {self.nome} | Salário Base: R$ {self.salario_base:.2f}")

# Criando um objeto
novo_funcionario = Funcionario("Alice", 4500.00)
novo_funcionario.exibir_dados()

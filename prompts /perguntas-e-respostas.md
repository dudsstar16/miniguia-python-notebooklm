# 🗂️ Engenharia de Prompts & Cicatrizes do Projeto

Este documento registra a estratégia por trás da comunicação com o Google NotebookLM, as dificuldades encontradas ("cicatrizes"), as limitações da inteligência artificial e as soluções estruturadas para garantir respostas de alta fidelidade e sem alucinações.

---

## 🧠 Metodologia de Prompting Utilizada

Para extrair respostas altamente interativas e ricas das fontes, estruturamos os prompts utilizando uma anatomia de **Engenharia de Prompts Contextual**:

1.  **Conteúdo Principal (Instruções):** Definição clara da tarefa e das restrições de comportamento (ex: "ajude-me a aprender de forma ativa", "não dê respostas diretas").
2.  **Contexto/Configuração:** Atribuição de papel à IA (ex: "aja como um professor de metodologias de programação em Python").
3.  **Conteúdo de Suporte:** Fornecimento de dados extras ou trechos específicos de fontes para enriquecer a geração do conteúdo.
4.  **Exemplos (Few-Shot & Zero-Shot Learning):** Demonstrações do formato exato de saída esperado para guiar o estilo de resposta da IA.
5.  **Especificação do Formato de Saída:** Uso de tabelas, blocos de código isolados e listas para evitar paredes de texto maçantes.

---

## ⚡ Histórico de Prompts Executados e Resultados

### 📌 Prompt 1: Estruturação do Guia para Iniciantes
> **Mensagem:** *Explique este conteúdo como se eu fosse iniciante. Gostaria de Dividir em partes, monte um guia de estudos, orientado ao aperfeiçoamento da linguagem de programação em python.*

*   **Técnica Aplicada:** Zero-Shot com instrução de estruturação sequencial.
*   **Resultado Obtido:** A IA dividiu o conhecimento em uma escada lógica de 5 níveis (Fundamentos, Variáveis, Coleções, Decisões/Repetições, Nível Profissional) e estruturou um cronograma sugerido de 10 semanas.

### 📌 Prompt 2: Metodologia de Aula Ativa e Desafios
> **Mensagem:** *Mostre exemplos práticos utilizando Python. Interaja como se fosse um professor profissional em metodologias da linguagem de programação em Python. Crie exercícios interativos para não tornar as abordagens apenas em textos.*

*   **Técnica Aplicada:** Role-playing (Atribuição de Persona) combinado com pedido de interatividade.
*   **Resultado Obtido:** Criação de módulos práticos de competência (com exemplos funcionais em Python) e geração de 4 desafios com perguntas reflexivas e de código.

### 📌 Prompt 3: Plano de Estudos para Rotinas Restritas
> **Mensagem:** *Monte um plano de estudos baseado neste material, em que se baseia em uma rotina de uma semana, inicialmente. Para um individuo que trabalha 6 horas por dia, organize uma rotina de estudos de sucesso, baseado no passo a passo dos modulos que será estudados, conforme citado acima.*

*   **Técnica Aplicada:** Prompting baseado em restrição de cenário real (tempo de trabalho do usuário).
*   **Resultado Obtido:** Divisão diária milimetrada focada em consistência (1.5h a 2h de estudo ativo por dia), com orientações de execução linear e versionamento do progresso.

---

## 🩸 "Cicatrizes" do Processo & Troubleshooting (Dificuldades Encontradas)

Durante a fase de testes e refinamento da base de conhecimento, deparamo-nos com alguns desafios de comportamento do LLM:

*   **Ambiguidade por Overload de Prompt:** Prompts excessivamente longos ou com instruções conflitantes faziam a IA misturar conceitos ou ignorar as fontes locais, chegando a gerar fontes alucinadas.
    *   *Como contornei:* Reduzi o escopo de cada prompt. Passamos a trabalhar de forma incremental e modular.
*   **Monotonia de Formato (Excesso de Texto):** Mesmo solicitando interatividade múltiplas vezes, a IA insistia em responder com grandes blocos de texto corrido.
    *   *Como contornei:* Passei a exigir formatos de saída específicos (tabelas, bullet-points limitados, blocos de código curtos) e técnicas de *Few-Shot Learning* (mostrando exemplos visuais do que eu considerava "interativo").
*   **Fadiga de Repetição:** Ter que reapresentar o contexto de saída e as restrições (ex: "não dê a resposta de bandeja", "use Markdown") a cada novo script de exercício gerado era ineficiente.
    *   *Como contornei:* Utilização de notas estruturadas fixas no painel do NotebookLM para servir de "gabarito comportamental" para a IA.
*   **Latência na Leitura:** Tempo de processamento elevado na primeira indexação e sincronização de novas fontes.

---

## 🛑 Limitações Identificadas na IA (NotebookLM)

*   **Contexto Histórico Limitado (Memory Drift):** À medida que o chat se estende, a IA tende a esquecer a persona de "Professor Ativo de Python" e precisa ser constantemente lembrada do papel que está desempenhando.
*   **Limites do Plano Gratuito:** O limite no volume e tamanho de arquivos importados como fonte exige uma curadoria manual muito mais rígida do que o necessário.

---

## 📈 Melhores Práticas Consolidadas para o Repositório

Para garantir que a base de conhecimento do NotebookLM continue precisa, adotamos a regra de **Instruções Multicamadas**:

```text
[Contexto / Papel] ➔ [Conteúdo Principal] ➔ [Restrições / Indicações] ➔ [Exemplo de Saída Esperado]

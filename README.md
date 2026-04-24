# Agente de Itinerário Inteligente

<p align="center">
  <img src="./banner.png" alt="Logo do projeto" width="700" />
</p>

**Projeto Final** — Agentes de IA com LangGraph  
Especialização em Inteligência Artificial Aplicada — IFG  

**Equipe:** Eduardo Braga, Israel Magalhães, Marcelo Carvalho

---

## Sobre

Agente de IA construído com **LangGraph** que recebe um destino de viagem, consulta o clima atual via API externa e gera um roteiro de 1 dia adequado ao clima. Se o roteiro proposto não condiz com o clima (ex: praia em dia de chuva), o agente rejeita e refaz automaticamente — até 3 tentativas.

```
Pesquisador (clima) → Planejador (roteiro) → Validador
                            ↑                    │
                            └── se rejeitado ────┘
```

## Arquitetura

| Nó | Responsabilidade | Tecnologia |
|---|---|---|
| **Pesquisador** | Recebe o destino e busca o clima atual | API Open-Meteo |
| **Planejador** | Gera roteiro de 1 dia adequado ao clima | Groq Llama 3.3 70B (`temperature=0.7`) |
| **Validador** | Verifica se o roteiro condiz com o clima | Groq Llama 3.3 70B (`temperature=0`) |
| **Roteador** | Decide o próximo passo após o Validador | Função Python condicional |

O estado compartilhado (`AgentState`) é um `TypedDict` com os campos `local`, `clima_encontrado`, `itinerario` e `tentativas`. O ciclo é implementado via `add_conditional_edges` do LangGraph.

## Como executar

1. **Clonar o repositório:**
   ```bash
   git clone https://github.com/educbraga/agentes-de-ia-com-langgraph.git
   cd agentes-de-ia-com-langgraph
   ```

2. **Criar e ativar o ambiente virtual:**
   ```bash
   python -m venv .venv
   source .venv/bin/activate   # Mac/Linux
   .venv\Scripts\activate      # Windows
   ```

3. **Instalar dependências:**
   ```bash
   pip install langgraph langchain-core langchain-groq requests jupyter
   ```

4. **Criar uma chave da API Groq** (gratuita) em https://console.groq.com/keys

5. **Abrir o notebook e executar:**
   ```bash
   jupyter notebook projeto.ipynb
   ```
   No Jupyter: **Kernel → Restart & Run All**. A célula de configuração pedirá a `GROQ_API_KEY` via `getpass` — cole a chave quando solicitado (ela não é persistida no notebook).

## Entregáveis

| Arquivo | Conteúdo |
|---|---|
| `projeto.ipynb` | Notebook com código comentado das 10 seções |
| `grafo.png` | Imagem do grafo compilado (saída da seção 8) |
| Logs do ciclo | Output das seções 9 e 10 após executar o notebook — mostram o Planejador sendo chamado novamente após rejeição do Validador |

## Critérios de avaliação atendidos

| Critério | Peso | Onde está |
|---|---|---|
| **Funcionalidade** | 40% | Grafo executa end-to-end (seção 9) sem erros de estado/tipo |
| **Uso de Ciclos** | 30% | `add_conditional_edges` (seção 7) + demonstração visível do ciclo (seção 10) |
| **Integração de API** | 20% | Open-Meteo usada no Pesquisador (seção 3), alimentando `state["clima_encontrado"]` |
| **Documentação** | 10% | Este README + comentários e docstrings nas células do notebook |

## Licença

MIT — ver `LICENSE`.

# Agente de Itinerário Inteligente

<p align="center">
  <img src="./banner.png" alt="Logo do projeto" width="700" />
</p>

**Projeto Final** — Agentes de IA com LangGraph </br>
Especializacao em Inteligencia Artificial Aplicada — IFG</br>

**Equipe:** Eduardo, Israel, Marcelo</br>
**Entrega:** Notebook + Codigo comentado + Log de execucao + Visualizacao do Grafo

---

```bash
python -m venv .venv
source .venv/bin/activate # Mac/Linux
.venv\Scripts\activate # Windows
```

---

## O Projeto

Um agente de IA que recebe um destino de viagem, busca o clima atual via API e gera um roteiro de 1 dia adequado ao clima. Se o roteiro nao condizer com o clima, o agente refaz automaticamente (ate 3 tentativas).

```
Pesquisador (clima) -> Planejador (roteiro) -> Validador
                             ^                    |
                             +--- (se rejeitado) -+
```

## Divisao do Trabalho

Cada um e responsavel por um bloco de secoes do notebook. Os blocos sao independentes: cada secao ja vem com um exemplo fixo de entrada para voce poder trabalhar sem depender de quem vem antes.

| Secoes do notebook                                              | Quem        | O que faz                                                           |
| --------------------------------------------------------------- | ----------- | ------------------------------------------------------------------- |
| 1. Setup/Imports + 2. AgentState + 3. Pesquisador               | **Marcelo** | Instalar libs, definir o state, buscar clima via API                |
| 4. Planejador + 5. Validador + 6. Roteador                      | **Israel**  | As funcoes que usam LLM (gerar roteiro e validar) + logica do ciclo |
| 7. Montagem do Grafo + 8. Visualizacao + 9. Execucao + 10. Demo | **Eduardo** | Montar o grafo, conectar os nos, executar e demonstrar o ciclo      |

## Como trabalhar de forma independente

Cada secao do notebook tem um **exemplo fixo de entrada** para voce testar sem precisar que a secao anterior esteja pronta:

- **Marcelo:** nao precisa esperar o Israel e o Eduardo. Use `local = "Rio de Janeiro"` para testar o Pesquisador.
- **Israel:** nao precisa esperar o Marcelo. Use `clima_encontrado = "Chuva forte, 22C"` para testar o Planejador e o Validador.
- **Eduardo:** nao precisa esperar ninguem. Use exemplos fixos de clima e itinerario para montar e testar o grafo.

Quando tudo estiver pronto, e so remover os exemplos fixos e conectar.

## Links de Estudo

### Todos

- O arquivo Projeto Final.pdf
- LangGraph overview: https://langchain-ai.github.io/langgraph/

### Marcelo

- O que e uma API: https://www.youtube.com/watch?v=Q-lyQ7BdDXE
- API Open-Meteo (testar no browser): https://open-meteo.com/en/docs
- Biblioteca `requests`: https://docs.python-requests.org/en/latest/user/quickstart/
- `@tool` do LangChain: https://python.langchain.com/docs/how_to/custom_tools/

### Israel

- Groq (criar API key gratuita): https://console.groq.com/keys
- ChatGroq no LangChain: https://python.langchain.com/docs/integrations/chat/groq/

### Eduardo

- LangGraph quickstart: https://langchain-ai.github.io/langgraph/tutorials/introduction/
- Conditional edges: https://langchain-ai.github.io/langgraph/how-tos/branching/

## Cronograma

| Quando | O que                                                        |
| ------ | ------------------------------------------------------------ |
| 1      | Cada um estuda seus links e implementa sua parte no notebook |
| 2      | Eduardo integra e o grupo testa                              |

## Observacao

- Se travar, pede ajuda no grupo

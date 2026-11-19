# BUS NOW — Citizen Tech

**Faculdade de Informática e Administração Paulista (FIAP)**
Ciências da Computação — Pensamento Computacional e Automação em Python
**Global Solution 2026** — São Paulo
---

##  Integrantes
| Nome | RM |
|------|----|
| Thor Correa Neto | 575726 |
| Tales de Souza Jardim | 575080 |
---

## Introdução
O projeto BUS NOW busca solucionar a superlotação e a distribuição inadequada de ônibus no transporte público, problemas que afetam o dia a dia de quem depende do transporte coletivo. Seu público beneficiado é formado principalmente pelos passageiros e pelos profissionais responsáveis pelo gerenciamento e pela distribuição da frota. O objetivo do programa, desenvolvido em Python, é monitorar a quantidade de pessoas em diferentes pontos, comparar a demanda com a capacidade dos ônibus e classificar a prioridade de cada local (alta, média ou baixa), indicando onde é necessário reforçar a frota. O projeto está relacionado ao ODS 11 – Cidades e Comunidades Sustentáveis, da ONU, que trata de sistemas de transporte seguros, acessíveis e sustentáveis, contribuindo para a melhoria da mobilidade urbana e da qualidade de vida da população.
---

##  Instruções de execução
Requisitos: Python 3 instalado. Não há bibliotecas externas.

```bash
python main.py
```

Menu principal:

```
======= CITIZEN TECH =======
--- BUS NOW ---
1 - Cadastrar dados
2 - Consultar relatorio
3 - Encerrar
```

### Cadastrar dados (opção 1)
O programa solicita, nesta ordem:

1. **Ponto** (1 a 4);
2. **Quantidade de pessoas** aguardando;
3. **Horário** (hora inteira, ex.: `13`);
4. **Ônibus em circulação**;
5. **Ônibus parados** (no pátio).

Ao final, exibe a **prioridade** do ponto e uma **recomendação** de ação.

### Consultar relatório (opção 2)

Lista todos os registros cadastrados na sessão e exibe os indicadores gerais.

### Pontos monitorados e referências

A referência é a quantidade estimada, pré-estabelecida, de passageiros que costumam utilizar ônibus em cada ponto.

| # | Ponto | Referência (pessoas) |
|---|-------|----------------------|
| 1 | FIAP | 21 |
| 2 | Parque | 45 |
| 3 | Shopping | 60 |
| 4 | Metrô | 100 |

---

## 📐 Regras de classificação

**Premissas da simulação**

- Capacidade do ponto = `ônibus em circulação × 40` (padrão de micro-ônibus);
- **Horário de pico** (média de São Paulo): **6h–9h** e **17h–20h**.

**Pontuação de prioridade**

| Critério | Condição | Pontos |
|----------|----------|:------:|
| Referência do ponto | pessoas > 150% da referência | +3 |
| Referência do ponto | pessoas > referência (até 150%) | +2 |
| Capacidade da frota | pessoas > capacidade | +3 |
| Capacidade da frota | em horário de pico e pessoas ≥ 80% da capacidade | +2 |
| Horário | está em horário de pico | +2 |

**Classificação final**

| Pontuação total | Prioridade |
|:---------------:|:----------:|
| 6 ou mais | 🔴 **ALTA** |
| 3 a 5 | 🟡 **MÉDIA** |
| 0 a 2 | 🟢 **BAIXA** |

**Recomendação de ação**

- Se `pessoas > capacidade` **ou** (pico **e** `pessoas ≥ 80% da capacidade`):
  - com ônibus parados no pátio → *"Enviar ônibus do pátio"*;
  - sem ônibus no pátio → *"Solicitar mais ônibus para o local"*;
- Caso contrário → *"Não há necessidade de ação, frota suficiente"*.

---

## 📊 Descrição dos resultados

A cada cadastro, o programa informa a prioridade do ponto e a recomendação para a frota.

No relatório (opção 2), são exibidos, para cada registro: ponto, passageiros, horário, ônibus em circulação, ônibus parados e prioridade. Em seguida, os **indicadores**:

- **Total de passageiros** registrados;
- **Média de passageiros** por registro;
- **Quantidade de registros de alta prioridade**.

Por fim, é apresentada uma conclusão:

- Se há registros de prioridade ALTA → *"existem pontos que precisam de atenção urgente"*;
- Caso contrário → *"Nenhum ponto apresenta alta prioridade"*.

Assim, o gestor da frota consegue identificar rapidamente onde reforçar o atendimento, reduzindo a superlotação e melhorando a distribuição dos ônibus.

# Análise Comparativa de Backcasting do Índice de Gini (1872-2022)

[![Python 3.12+](https://img.shields.io/badge/Python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![Julia 1.10+](https://img.shields.io/badge/Julia-1.10+-purple.svg)](https://julialang.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 1. Visão Geral

Este projeto é uma simulação econométrica que compara o desempenho de múltiplos modelos estatísticos e de machine learning em uma tarefa de **backcasting** (retroprojeção).

O pipeline completo está contido  no notebook *Simulação.ipynb*, que executa as seguintes etapas:
1.  **Simula** uma série temporal de 151 anos (1872-2022) para o Índice de Gini e covariáveis (PIB, Urbanização, etc.), com regimes estruturais e tendências complexas.
2.  **Separa** os dados em um período "Moderno" (1976-2022), simulando a disponibilidade de dados (ex: PNAD), e um período "Histórico" (1872-1975), que serve como "verdade oculta" (ground truth).
3.  **Treina** seis classes diferentes de modelos *exclusivamente* nos dados modernos.
4.  **Usa** esses modelos para "retro-projetar" (backcast) o período histórico.
5.  **Compara** as projeções com a "verdade oculta" para determinar qual modelo melhor captura a dinâmica de longo prazo, mesmo com informações limitadas.

## 2. Modelos Comparados

O pipeline treina, avalia e compara os seguintes modelos:

1.  **Regressão Linear (OLS)**: O modelo de baseline, assume relações lineares e estáveis.
2.  **Regressão com Mudança de Regime de Markov (MSR)**: Um modelo econométrico que permite que os coeficientes e a variância mudem de acordo com "estados" ocultos (regimes).
3.  **Modelos Aditivos Generalizados (GAMs)**: Um modelo de machine learning interpretável que captura relações não-lineares complexas através de *splines*.
4.  **Modelo de Série Temporal Estrutural (UCM)**: Um modelo que decompõe a série em tendência, ciclo e sazonalidade, e usa a dinâmica aprendida para o backcasting (via inversão da série).
5.  **Modelo Bayesiano Hierárquico**: Um modelo probabilístico (`PyMC`) que inclui uma tendência de passeio aleatório (random walk) para capturar movimentos estocásticos de longo prazo.
6.  **Otimização Quântica (QAOA)**: Um modelo "proof-of-concept" que usa o Quantum Approximate Optimization Algorithm (QAOA) para *resolver* o problema de regressão linear, demonstrando uma abordagem de otimização híbrida quântico-clássica.

## 3. Como Executar

Este projeto foi desenvolvido em Python 3.12+ em um ambiente WSL (Ubuntu).

## 4. Bônus

O notebook *Simulação - Bayesiana(Julia).ipynb* contém a simulação de backcasting para **Modelo Bayesiano Hierárquico**, com a finalidade de obter um benchmarking de tempo de execução. Ele não precisa ser executado em WSL>

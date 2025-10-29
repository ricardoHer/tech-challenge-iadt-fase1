# Tech Challenge IADT – Fase 1

Sistema inteligente de suporte ao diagnóstico utilizando o dataset **Breast Cancer Wisconsin (Diagnostic)**.

## Objetivo

Treinar e avaliar modelos de machine learning capazes de classificar tumores mamários como benignos ou malignos, priorizando **recall** para evitar falsos negativos.

## Estrutura

- notebooks/ — exploração, modelagem e interpretação
- src/ — scripts de data loading, preprocessamento e avaliação
- docker/ — arquivos de containerização
- data/ — datasets locais (ignorados pelo git)

## Execução local

```bash
python -m venv .venv
source .venv/bin/activate   # ou .venv\\Scripts\\activate no Windows
pip install -r requirements.txt
jupyter lab
```

## Dataset

Disponível via sklearn.datasets.load_breast_cancer().

## Autores

Ricardo Franco Hernandez – Pós-graduação FIAP – Inteligência Artificial para Devs

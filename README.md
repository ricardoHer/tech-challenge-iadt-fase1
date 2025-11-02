# Tech Challenge IADT – Fase 1

Sistema inteligente de suporte ao diagnóstico usando o dataset **Breast Cancer Wisconsin (Diagnostic)**.

## Visão geral

Este repositório contém notebooks e código-fonte para explorar, pré-processar e treinar modelos de classificação (ex.: RandomForest, XGBoost) que detectam tumores mamários benignos vs. malignos. O trabalho prioriza métricas que minimizem falsos negativos (alta recall) por razões clínicas.

## Objetivo

Treinar, validar e comparar modelos de machine learning para classificação binária do dataset, com foco em:

- Pipeline reproduzível de pré-processamento (scaling, imputação, encoding quando necessário).
- Avaliação baseada em validação estratificada e métricas: recall, precision, ROC AUC, matrizes de confusão.
- Interpretabilidade básica (SHAP) para entender importância de features quando aplicável.

## Estrutura do projeto

- `notebooks/` — notebooks organizados por objetivo: EDA, pré-processamento, modelagem, interpretabilidade.
- `src/` — código reusável (carregamento de dados, transformações, treinamento e avaliação).
- `data/` — arquivos de dados locais (pasta versionada como vazia/ignored por git; contém `raw/` e `processed/`).
- `docker/` — Dockerfile e artefatos para rodar o projeto em container.

> Observação: mantive a estrutura original e informações existentes — notebooks, src, docker e data continuam como organizados.

## Requisitos e compatibilidade

- O arquivo `requirements.txt` contém versões fixas das dependências usadas durante o desenvolvimento.
- Recomenda-se usar Python 3.10, 3.11 ou 3.12 para máxima compatibilidade com bibliotecas científicas (XGBoost e outras podem apresentar problemas em Python 3.13).
- Se estiver em macOS, instale o Python 3.12 via Homebrew: `brew install python@3.12` e aponte para `python3.12` ao criar o ambiente.

Observação sobre XGBoost: se você receber erros do tipo `XGBoostError` relacionados à arquitetura ou compatibilidade (por exemplo em Python 3.13), crie um ambiente com Python 3.12/3.11 e reinstale dependências.

## Quickstart — execução local

1. Abra um terminal na raiz do projeto.  
2. Crie e ative um ambiente virtual (exemplo macOS / Linux):

```bash
python3.12 -m venv .venv
source .venv/bin/activate   # ou .venv\Scripts\activate no Windows
```

3. Atualize pip e instale dependências:

```bash
pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
```

4. Instale o kernel do ipykernel (opcional, para selecionar facilmente no Jupyter/VS Code):

```bash
pip install ipykernel
python -m ipykernel install --user --name tech-challenge-venv --display-name "Python 3.12 (tech-challenge)"
```

5. Inicie o Jupyter Lab:

```bash
jupyter lab
```

6. No VS Code, selecione o interpretador/kernel correspondente ao ambiente `.venv` (Command Palette → Python: Select Interpreter).

## Execução via Docker

```bash
docker build -t tech-challenge-fase1 -f docker/Dockerfile .
docker run -p 8888:8888 tech-challenge-fase1
```

O container expõe o Jupyter Lab na porta 8888 por padrão (ver `docker/Dockerfile` para configuração adicional).

## Notebooks principais

- `00-setup.ipynb` — verificação do ambiente e primeiras importações.
- `01-eda.ipynb` — exploração e visualização dos dados.
- `02-preprocess-models.ipynb` — pipelines, treinamento e comparação de modelos.
- `03-advanced-models.ipynb` — experimentos com modelos avançados (ex.: XGBoost, tuning).
- `04-interpretability.ipynb` — análise de interpretabilidade (SHAP, feature importances).

## Dados

O dataset original usado é acessível via `sklearn.datasets.load_breast_cancer()`. Para reprodutibilidade armazenamos dados processados em `data/processed/` quando apropriado. Não versionamos dados brutos sensíveis.

## Testes e qualidade

Atualmente não há uma suíte de testes automatizados nesta fase. Como próximos passos sugeridos:

- Adicionar testes unitários para funções em `src/` (pytest).
- Incluir CI simples para checagem de lint e execução rápida de notebooks (nbconvert).

## Contribuição

Pull requests são bem-vindos — abra uma issue para discutir mudanças significativas antes de implementá-las. Mantenha o estilo de código consistente e documente quaisquer novas dependências.

## Autor

RM368872 - Ricardo Franco Hernandez – Pós-graduação FIAP – Inteligência Artificial para Devs

> 💡 Observação: as versões no `requirements.txt` foram escolhidas para compatibilidade entre macOS, Windows e Linux. Caso encontre incompatibilidades (especialmente com Python 3.13), prefira criar um ambiente com Python 3.12.
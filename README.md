# Tópicos Avançados em Inteligência Artificial - Laboratórios

Este repositório contém os materiais práticos (Jupyter Notebooks) e os scripts de apoio para a geração de figuras para o material da disciplina de **Tópicos Avançados em Inteligência Artificial**.

## 📂 Estrutura do Repositório

*   `aula_03_estatistica/`: Contém os notebooks da Aula 3, abordando conceitos fundamentais de estatística para Ciência de Dados e IA. Os arquivos com o prefixo `figura_` são scripts focados na produção de figuras didáticas para o material da disciplina.
    *   `01_figura_exploratory_data_analysis.ipynb`: Script de Análise Exploratória de Dados (EDA) para material didático.
    *   `02_figura_cdf_teste_ks.ipynb`: Script visual sobre Função Cumulativa de Distribuição (CDF) e Teste de Kolmogorov-Smirnov (KS).
    *   `03_teste_de_hipotese.ipynb`: Notebook prático sobre Fundamentos de Testes de Hipótese.
    *   `04_figura_normal_vs_t_student.ipynb`: Script visual de comparação entre as distribuições Normal e T de Student.
    *   `05_teste_hipotese_unilateral.ipynb`: Notebook prático sobre Testes de Hipótese Unilaterais.
*   `data/`: Diretório ignorado no versionamento (`.gitignore`) que deverá abrigar os conjuntos de dados utilizados nos laboratórios (ver seção *Datasets* abaixo).
*   `outputs/`: Diretório destinado ao armazenamento de gráficos e resultados gerados durante a execução dos scripts (ex: `outputs/figures/`).

## 📊 Datasets

Para manter o repositório leve e otimizado, os conjuntos de dados (arquivos `.csv`, `.zip`, etc.) **não são versionados neste repositório**. 

Para executar os notebooks que dependem de dados reais, você deverá baixar os datasets correspondentes listados abaixo e inseri-los no diretório `data/` localmente:

*   **Ames Housing Dataset:** 
    * O dataset de preços de imóveis utilizado em nossos estudos é oriundo de uma competição do Kaggle. 
    * Link para download: [House Prices - Advanced Regression Techniques (Kaggle)](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)
    * Baixe o arquivo e extraia-o dentro de uma subpasta (ex: `data/ames_housing/`).

## 🚀 Como Executar os Laboratórios

Para reproduzir os experimentos na sua máquina local, siga os passos abaixo:

### 1. Pré-requisitos

Certifique-se de ter o [Python](https://www.python.org/) instalado em seu sistema (versão 3.8 ou superior recomendada). O uso de ambientes virtuais (como `venv` ou `conda`) é fortemente aconselhado.

### 2. Configurando o Ambiente

Abra o terminal ou prompt de comando, navegue até a pasta raiz deste projeto (`Lab/`) e execute:

#### 2.1. Criando o ambiente virtual (opcional, mas recomendado)

```bash
python -m venv venv
```

##### 2.1.1 Ativando o ambiente virtual - Windows

```bash
venv\Scripts\activate
```

##### 2.1.2 Ativando o ambiente virtual - Linux/macOS

```bash
source venv/bin/activate
```

#### 2.2. Instalando as dependências

```bash
pip install -r requirements.txt

# Registre o ambiente virtual como um Kernel no Jupyter
python -m ipykernel install --user --name=venv_ia --display-name="Python (TAIA Lab)"
```


### 3. Executando o Jupyter

Com o ambiente configurado, inicie o servidor do Jupyter:

```bash
jupyter notebook
# Ou
jupyter lab
```

Uma aba será aberta no seu navegador. Navegue até a pasta da aula para acompanhar os materiais.

> 💡 **IMPORTANTE:** Ao abrir um Notebook pela primeira vez no Jupyter Lab, certifique-se de selecionar o kernel **"Python (TAIA Lab)"** no canto superior direito para que ele utilize todas as dependências do ambiente virtual corretamente.

## ⚠️ Problemas Conhecidos

Está enfrentando algum erro de "PSSecurityException" ou "MAX_PATH" durante a configuração? 
Consulte nosso guia de resolução de problemas no arquivo [TROUBLESHOOTING.md](TROUBLESHOOTING.md) para soluções detalhadas.

---
*Professor: Miller Horvath*
*Instituição: Gran Faculdade*

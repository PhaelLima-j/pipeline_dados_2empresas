# 🐧 Ambiente Linux com WSL

Este guia tem como objetivo registrar a criação e organização de um ambiente Linux utilizando o **WSL (Windows Subsystem for Linux)**, voltado para o desenvolvimento de projetos de **engenharia de dados**.

---

## 📁 Estruturando Diretórios

### ✅ Comandos Básicos

```bash
ls                  # Lista arquivos e pastas do diretório atual
mkdir nome_pasta    # Cria uma nova pasta
cd nome_pasta       # Entra no diretório especificado
```

### 📂 Exemplo prático

```bash
$ mkdir Documentos
$ cd Documentos
$ mkdir pipeline_dados
$ cd pipeline_dados

# Estrutura de diretórios do projeto
$ mkdir data_raw data_processed notebooks scripts
$ ls
data_processed  data_raw  notebooks  scripts
```

> 💡 Para baixar arquivos diretamente em uma pasta, utilize:
> `wget <URL_DO_ARQUIVO>`

---

## 🔧 Atualizando e Instalando Pacotes no WSL

### Atualizando o sistema:

```bash
sudo apt-get update
sudo apt-get upgrade -y
```

### Verificando a versão do Python:

```bash
python3 --version
# ou
python3 -V
```

### Instalando ferramentas essenciais:

```bash
sudo apt install python3-pip -y       # Gerenciador de pacotes Python
sudo apt install python3-venv -y      # Módulo para ambientes virtuais
```

---

## 🐍 Criando um Ambiente Virtual Python

Um **ambiente virtual** permite isolar as bibliotecas e dependências de cada projeto.

### Passo a passo:

1. Crie e acesse o diretório do projeto:

```bash
mkdir pipeline_dados
cd pipeline_dados
```

2. Crie o ambiente virtual:

```bash
python3 -m venv venv
```

3. Ative o ambiente:

```bash
source venv/bin/activate
```

4. Instale bibliotecas essenciais:

```bash
pip install requests==2.28.2
pip install pandas==2.0.0
```

### Dicas Adicionais

* Para **desativar** o ambiente virtual:

  ```bash
  deactivate
  ```

* Para **salvar as dependências** do projeto:

  ```bash
  pip freeze > requirements.txt
  ```

* Para **instalar as dependências** salvas:

  ```bash
  pip install -r requirements.txt
  ```

---

## 📅 Configurando o VS Code com WSL

1. No terminal WSL, navegue até o diretório do projeto e execute:

   ```bash
   cd pipeline_dados
   code .
   ```

2. No VS Code:

   * Acesse a aba "Extensions"
   * Busque por "WSL"
   * Instale a extensão com o ícone do pinguim azul chamada "WSL"

3. Ao abrir o VS Code novamente via terminal com `code .`, verifique se a sinalização **WSL: Ubuntu-22.04** aparece no canto inferior esquerdo.

A extensão permite usar o VS Code no Windows para criar aplicativos Linux diretamente via WSL.

---

## 📁 Organização de Pastas em Projetos de Engenharia de Dados

* **data\_raw**: Contém os dados originais (brutos).
* **data\_processed**: Contém os dados já tratados ou transformados.
* **scripts**: Scripts em Python ou outra linguagem.
* **notebooks**: Jupyter Notebooks para exploração e análise dos dados.

> 💭 Importante: mantenha um padrão de organização para facilitar a manutenção e colaboração em equipe.

---

## 📃 Leitura de Arquivos CSV e JSON em Python

### 1. Importando bibliotecas:

```python
import csv
import json
```

### 2. Leitura de CSV com DictReader:

```python
with open('seuarquivo.csv', 'r') as arquivo_csv:
    leitor_csv = csv.DictReader(arquivo_csv)
    for linha in leitor_csv:
        print(linha['nome_coluna'])
```

### 3. Leitura de JSON com json.load():

```python
with open('seuarquivo.json', 'r') as arquivo_json:
    dados = json.load(arquivo_json)
    # Agora você pode trabalhar com os dados como um dicionário Python
```

### Considerações:

* **CSV** é ideal para dados tabulares.
* **JSON** é flexível e suporta estruturas aninhadas.
* Use `DictReader` para acessar colunas por nome.
* Cuidado ao carregar arquivos JSON grandes, pois o `json.load()` carrega todo o arquivo na memória.

---

## ✅ Conclusão

Com este ambiente devidamente configurado e organizado, você está pronto para iniciar seus projetos de engenharia de dados com mais eficiência, clareza e boas práticas.

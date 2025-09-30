# Documentação do Código-QL

Este repositório contém o código-fonte da documentação oficial para colaboradores do projeto **Código-QL**. O site é construído com [MkDocs](https://www.mkdocs.org/) e o tema [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/).

---

## 🚀 Acessando a Documentação

A documentação completa, com todos os tutoriais e políticas de contribuição, está disponível publicamente no nosso site.

**➡️ [Acesse o site da documentação aqui](https://codigo-ql.github.io/CodigoQL-Documentacao/)**

---

## 🛠️ Rodando o Projeto Localmente

Se você deseja contribuir com a documentação ou apenas visualizá-la em sua máquina local, siga os passos abaixo.

### Pré-requisitos

-   [Python 3.x](https://www.python.org/)
-   `pip` (gerenciador de pacotes do Python)

### Passos para Instalação

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/Codigo-QL/CodigoQL-Docs.git](https://github.com/Codigo-QL/CodigoQL-Docs.git)
    cd CodigoQL-Docs
    ```

2.  **(Recomendado) Crie e ative um ambiente virtual:**
    ```bash
    # Cria o ambiente
    python3 -m venv .venv

    # Ativa o ambiente (Linux/macOS)
    source .venv/bin/activate
    
    # Ativa o ambiente (Windows)
    # .\.venv\Scripts\activate
    ```

3.  **Instale as dependências:**
    ```bash
    pip install mkdocs-material
    ```

4.  **Inicie o servidor local:**
    ```bash
    mkdocs serve
    ```

    O site estará disponível em `http://127.0.0.1:8000`. O servidor recarregará a página automaticamente sempre que você salvar uma alteração nos arquivos.
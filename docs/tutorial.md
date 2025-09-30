# **Tutorial Completo: Adicionando Conteúdo ao Código-QL**

Este guia é o seu ponto de partida para criar e adicionar novos capítulos e níveis à plataforma. O processo foi desenhado para ser simples, focando na edição de arquivos de texto e na adição de mídias.

## **Visão Geral do Processo**

> **Importante:** Todas as contribuições de conteúdo, incluindo a edição dos arquivos `.json` e a adição de novos arquivos de imagem (`.webp`) e banco de dados (`.sqlite`), devem ser feitas **exclusivamente** no repositório de banco de dados do projeto.

> **Repositório de Conteúdo:** [**Codigo-QL/CodigoQL-DataBase**](https://github.com/Codigo-QL/CodigoQL-DataBase)

> Siga as instruções de configuração (`README.md`) desse repositório para preparar seu ambiente local antes de começar.

Adicionar conteúdo ao Código-QL envolve principalmente a edição de quatro arquivos `.json` na pasta `data/`:

1. `capitulos.json`: Para definir a história principal do seu capítulo.  
2. `personagens.json`: Para registrar os personagens que guiam a narrativa.  
3. `base_dados.json`: Para registrar os bancos de dados que seus exercícios usarão.  
4. `niveis.json`: Onde a mágica acontece, definindo cada exercício.

Você também poderá adicionar arquivos nas pastas `data/images/` (imagens dos personagens) e `data/files/` (os bancos de dados .sqlite).

## **Passo 1: Criando um Novo Capítulo**

Tudo começa com uma boa história. O capítulo é o contêiner da sua narrativa e agrupa uma sequência de níveis.

Para criar um capítulo, abra o arquivo `data/capitulos.json` e adicione um novo objeto JSON ao array.

### **Estrutura do Objeto Capítulo**

```json
// data/capitulos.json  
[  
  ...  
  {  
    "codigo": "C3",  
    "titulo": "O Mistério do Cais",  
    "descricao": "Uma série de desaparecimentos no cais da cidade levanta suspeitas de um novo serial killer...\\n\\n**Conteúdos abordados neste capítulo:**\\n\\n- Consultas com **SUBSELECT**\\n- Funções de data e hora\\n- **CASE WHEN**"  
  }  
]
```

### **Explicação dos Campos**

* "codigo": **(Obrigatório)** Um código **único** e curto para identificar seu capítulo. Use o padrão CX, onde X é o próximo número disponível.  
* "titulo": **(Obrigatório)** O nome do seu capítulo, que será exibido aos alunos.  
* "descricao": **(Obrigatório)** A sinopse da história. Este campo é uma **string que aceita formatação Markdown**.  
  * Use \\\\n para criar quebras de linha.  
  * **É de extrema importância** que você use Markdown para listar os conceitos de SQL que serão ensinados, como no exemplo (\*\*Conteúdos abordados...\*\*).

## **Passo 2: Construindo os Níveis**

Os níveis são os exercícios práticos que compõem seu capítulo. Antes de criá-los, você precisa definir dois elementos essenciais: o personagem que guiará o aluno e o banco de dados que ele irá consultar.

### **2.1 \- O Personagem que Conduz o Nível**

Cada nível é conduzido por um personagem, que apresenta a narrativa, dá dicas e fornece feedback.

#### **Usando um Personagem Existente**

Você pode usar qualquer personagem já definido no arquivo `data/personagens.json`. Basta usar o valor exato do campo `"nome"` ao criar seu nível.

#### **Criando um Novo Personagem**

Se sua história precisa de alguém novo:

1. **Prepare a Imagem:**  
   * Crie uma imagem para o personagem no formato **.webp** para garantir que ela seja leve.  
   * **Importante:** O fundo da imagem deve ser **branco puro (\#FFFFFF)** para se mesclar perfeitamente com a interface da plataforma.  
   * Adicione o arquivo de imagem à pasta data/images/.  
2. **Registre o Personagem:**  
   * Abra o arquivo data/personagens.json e adicione um novo objeto.

```json
// data/personagens.json  
[  
  ...  
  {  
    "nome": "Detetive Kaito",  
    "imagem": "kaito.webp"  
  }  
]
```

### **2.2 \- O Banco de Dados do Nível (.sqlite)**

Os alunos farão as consultas em um banco de dados SQLite que você fornecerá.

* **Recomendação:** Vários níveis devem usar o **mesmo arquivo** de banco de dados. Isso cria uma sequência narrativa coesa, onde o aluno explora diferentes facetas do mesmo "universo de dados" para resolver um caso.

#### **Usando um Banco de Dados Existente**

Você pode usar qualquer banco já registrado em `data/base_dados.json`. Anote o "codigo" dele para usar na criação do nível.

#### **Criando um Novo Banco de Dados**

Se seu capítulo precisa de um conjunto de tabelas totalmente novo:

**Siga o tutorial abaixo para criar o arquivo `.sqlite`:**

Você pode usar qualquer ferramenta que gere um arquivo `.sqlite`. O método recomendado, por ser baseado em texto e facilmente versionável, é usar a ferramenta de linha de comando `sqlite3`.

**Pré-requisito**: Você precisa ter o [SQLite](https://www.sqlite.org/download.html) instalado em sua máquina para ter o comando sqlite3 disponível no terminal.

- Crie um arquivo `.sql`:

Crie um arquivo de texto simples (ex: `C3S1.sql`) onde você escreverá os comandos para criar as tabelas e inserir os dados.

```sql
-- Exemplo de conteúdo para C3S1.sql

CREATE TABLE barcos (
id INTEGER PRIMARY KEY,
nome TEXT NOT NULL,
tipo TEXT,
hora_chegada TEXT
);

INSERT INTO barcos (id, nome, tipo, hora_chegada) VALUES
(1, 'Estrela do Mar', 'Pesca', '18:30'),
(2, 'Vento Norte', 'Carga', '22:15'),
(3, 'Gaivota', 'Turismo', '23:00');
```

- Gere e Teste o Banco de Dados:

Abra um terminal e use o sqlite3 para executar seu script. É uma boa prática gerar primeiro um arquivo .db para testes.

```Bash
# Este comando cria 'teste.db' e executa os comandos de 'C3S1.sql' dentro dele
sqlite3 teste.db < C3S1.sql
```

Agora, você pode abrir o banco de dados para testar se tudo foi criado corretamente:

```Bash
# Abrir o console do sqlite3
sqlite3 teste.db
```

Dentro do console, você pode rodar comandos para verificar:

```
sqlite> .tables          -- Lista as tabelas criadas
sqlite> SELECT * FROM barcos; -- Verifica se os dados foram inseridos
sqlite> .exit            -- Sai do console
```

- Renomeie para a Versão Final:

Se os testes foram bem-sucedidos, renomeie o arquivo `.db` para `.sqlite` com o nome padrão e coloque-o na pasta `data/files/`.

```Bash
# Renomeia o arquivo de teste para o nome final
mv teste.db C3S1.sqlite
```

**Registre o Novo Banco de Dados:**

   * Abra o arquivo `data/base_dados.json` e adicione um novo objeto.

   Estrutura e Padrão do CódigoO campo "codigo" é crucial para a organização e segue um padrão estrito: CXSY.

   * #### **CX: Refere-se ao Capítulo. Por exemplo, C3 para o Capítulo 3\.**

   * **SY**: Refere-se à **Sequência** dentro daquele capítulo. Uma **"Sequência"** é um conjunto de níveis que compartilham o mesmo arquivo de banco de dados e dão continuidade a uma micro-história. Por exemplo, S1 para a primeira sequência. Portanto, C3S1 significa "Capítulo 3, Sequência 1".

```json
// data/base_dados.json  
[  
  ...  
  {  
    "codigo": "C3S1",  
    "nome": "Banco de Dados do Caso do Cais - Parte 1",  
    "arquivo": "C3S1.sqlite"  
  }  
]
```

### **2.3 \- Adicionando o Nível ao niveis.json**

Com o capítulo, personagem e banco de dados definidos, você está pronto para criar o nível. Abra `data/niveis.json` e adicione um novo objeto para cada exercício.

#### **Estrutura do Objeto Nível**

```json
{  
  "id": 25,  
  "codigo_cap": "C3",  
  "narrativa": "A primeira pista surge de um bilhete anônimo...\\n\\\n O texto do bilhete dizia: 'Procurem o barco que chegou por último'.",  
  "enunciado": "Recupere o nome de todos os barcos atracados no cais após as 22h.",  
  "dica": "Para filtrar por hora, você precisará de uma função de data. Lembre-se de como usar a cláusula **WHERE**.\\n\\nPara ver a estrutura da tabela, use o comando:\\n\\n```sql\nPRAGMA table_info(barcos);\\n```",  
  "personagem_nome": "Detetive Kaito",  
  "solucao": "SELECT nome FROM barcos WHERE hora_chegada > '22:00';",  
  "feedback_correto": "Ótimo trabalho! A lista revela um padrão suspeito. Parece que todos os barcos pertencem à mesma empresa.",  
  "feedback_errado": "Ainda não é isso. A testemunha foi clara sobre o horário. Tente revisar a condição do seu filtro de tempo.",  
  "codigo_base": "C3S1"  
}
```

#### **Explicação dos Campos do Nível**

* "id": **(Obrigatório)** Um número de identificação **único** para o nível. Verifique o id do último nível no arquivo e adicione 1\.  
* "codigo\_cap": **(Obrigatório)** O "codigo" do capítulo ao qual este nível pertence.  
* "narrativa": **(Obrigatório)** O texto da história que contextualiza o exercício. Aceita **formatação Markdown** e \\\\n para quebras de linha.  
* "enunciado": **(Obrigatório)** A instrução direta e objetiva do que o aluno precisa fazer com a consulta SQL.  
* "dica": **(Obrigatório)** Ajuda contextual fornecida pelo personagem. Aceita **formatação Markdown**, não utilize \`\` para destacar termos técnicos, use \*\* no lugar. **É obrigatório** incluir o comando `PRAGMA table_info(nome_da_tabela);` dentro de um bloco de código (usando \`\`\`sql ... \`\`\`) para cada tabela necessária para a solução.  
* "personagem\_nome": **(Obrigatório)** O nome exato do personagem (definido em personagens.json) que está conduzindo este nível.  
* "solucao": **(Obrigatório)** A string contendo a consulta SQL correta que resolve o exercício.  
* "feedback\_correto": **(Obrigatório)** A mensagem que o personagem dirá ao aluno quando ele acertar. Deve ter relação com a narrativa.  
* "feedback\_errado": **(Obrigatório)** A mensagem que o personagem dirá quando o aluno errar.  
* "codigo\_base": **(Obrigatório)** O "codigo" do banco de dados (definido em base\_dados.json) que este nível utilizará.

## **Passo 3: Teste e Submeta sua Contribuição**

Depois de adicionar todas as suas alterações nos arquivos json e incluir os novos arquivos `.webp` e `.sqlite` (se houver):

1. **Teste Localmente:** Abra um terminal na raiz do projeto codigoql-database e rode o comando `npm run prisma-seed`. Isso irá ler seus arquivos e tentar adicionar os dados ao banco. Fique atento a qualquer mensagem de erro.  
2. **Envie:** Se tudo funcionar, siga as **[Políticas de Contribuição](contributing.md)** para criar uma branch, fazer o commit das suas alterações e abrir um Pull Request.

Sua contribuição será revisada e, se aprovada, fará parte do universo do Código-QL\!
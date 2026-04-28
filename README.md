# Sistema de Gestão de Jogadores (CRUD Python + Oracle)

Este é um programa de linha de comando (CLI) desenvolvido em Python para realizar o gerenciamento completo de jogadores de futebol, integrando-se diretamente com um banco de dados **Oracle**.

## 🚀 O que o programa faz?

O programa é um **CRUD** (Create, Read, Update, Delete), o que significa que ele gerencia o ciclo de vida completo dos dados de um jogador:

1.  **Cadastrar (Create):** Permite inserir um novo jogador informando Nome, Idade, Posição e Time.
2.  **Listar (Read):** Exibe na tela todos os jogadores salvos no banco de dados, organizados por ID.
3.  **Atualizar (Update):** Permite mudar o time de um jogador específico (útil para registrar transferências).
4.  **Excluir (Delete):** Remove permanentemente o registro de um jogador do banco de dados através do seu ID.

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python 3.x
* **Banco de Dados:** Oracle Database (suporta versões 12c, 19c, 21c e instâncias na nuvem/OCI).
* **Driver:** `oracledb` (a biblioteca oficial e mais moderna da Oracle para Python).

## 📋 Pré-requisitos

Antes de rodar o programa, você precisará:

1.  Ter o **Python** instalado.
2.  Instalar a biblioteca do driver Oracle:
    ```bash
    pip install oracledb
    ```
3.  Ter acesso a um banco de dados Oracle (usuário, senha e a string de conexão/DSN).

## ⚙️ Como Configurar

1.  Abra o arquivo `crud_jogadores.py`.
2.  Localize as variáveis de configuração no topo do arquivo:
    ```python
    USUARIO = "seu_usuario"
    SENHA = "sua_senha"
    DSN = "localhost:1521/xe"
    ```
3.  Substitua pelos dados do seu ambiente.

## 🗄️ Estrutura da Tabela

Ao iniciar pela primeira vez, o programa tentará criar automaticamente a tabela `jogadores` com as seguintes definições:

| Campo | Tipo | Descrição |
| :--- | :--- | :--- |
| **ID** | NUMBER | Chave primária (auto-incremento) |
| **NOME** | VARCHAR2(100) | Nome do atleta |
| **IDADE** | NUMBER | Idade do atleta |
| **POSICAO** | VARCHAR2(50) | Posição (Ex: Atacante, Goleiro) |
| **TIME** | VARCHAR2(100) | Clube atual |

## 🛡️ Segurança e Boas Práticas

* **Bind Variables:** O código utiliza variáveis de ligação (`:1, :2`) para evitar **SQL Injection**, garantindo que o banco de dados trate os inputs do usuário apenas como dados e não como comandos.
* **Tratamento de Conexão:** O programa abre e fecha conexões de forma segura para evitar vazamento de memória ou travamento de sessões no Oracle.
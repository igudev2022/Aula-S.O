# Guia Prático de Git e GitHub

## 1. Introdução

O Git é um sistema de controle de versões utilizado para acompanhar as alterações realizadas em arquivos de um projeto.

O GitHub é uma plataforma onde os repositórios Git podem ser armazenados na internet. Ele facilita o compartilhamento de projetos, o trabalho em equipe e o armazenamento de diferentes versões dos arquivos.

Neste guia serão apresentados os principais procedimentos para:

- Instalar e configurar o Git.
- Verificar se o Git está funcionando.
- Criar e clonar repositórios.
- Entrar na pasta de um projeto.
- Verificar alterações.
- Adicionar arquivos para o commit.
- Criar commits.
- Enviar alterações para o GitHub.
- Atualizar o projeto local.
- Trabalhar com branches.
- Resolver conflitos básicos.
- Utilizar o Git pelo Visual Studio Code.
- Seguir boas práticas de organização.

---

# 2. O que é Git?

Git é um sistema distribuído de controle de versão.

Ele permite registrar alterações feitas em um projeto ao longo do tempo. Dessa maneira, é possível acompanhar o histórico dos arquivos e retornar para versões anteriores quando necessário.

Um projeto utilizando Git possui um repositório local, que fica no computador do usuário.

Exemplo:

    Computador
        |
        +-- Projeto
             |
             +-- arquivo1.cpp
             +-- arquivo2.md
             +-- README.md
             +-- .git

A pasta `.git` contém informações utilizadas pelo Git para controlar o histórico do projeto.

---

# 3. O que é GitHub?

GitHub é uma plataforma utilizada para hospedar repositórios Git.

Um projeto pode existir tanto no computador quanto no GitHub.

    REPOSITÓRIO LOCAL
           |
           | git push
           v
         GITHUB
           |
           | git pull
           v
    REPOSITÓRIO LOCAL

O computador possui uma cópia local do projeto, enquanto o GitHub pode armazenar uma cópia remota.

---

# 4. Diferença entre Git e GitHub

Git e GitHub estão relacionados, mas não são a mesma coisa.

| Git | GitHub |
|---|---|
| Sistema de controle de versão | Plataforma de hospedagem |
| Funciona no computador | Funciona pela internet |
| Controla versões dos arquivos | Armazena repositórios remotamente |
| Possui comandos como `commit` e `branch` | Possui recursos como Pull Request e Issues |
| Pode funcionar sem internet | Normalmente é utilizado para colaboração online |

---

# 5. Configuração inicial do Git

Antes de utilizar os comandos do Git, é necessário instalar o programa no computador.

Depois da instalação, abra o terminal.

## 5.1 Verificando a instalação

Digite:

```bash
git --version

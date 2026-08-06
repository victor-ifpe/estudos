# C02 — Controle e Versionamento do Projeto com Git

## Objetivos da Aula

Ao final desta aula, o estudante deverá ser capaz de:

- Compreender o conceito de controle de versão;
- Entender a importância do versionamento em projetos de software;
- Diferenciar sistemas de versionamento centralizados e distribuídos;
- Conhecer o funcionamento do Git;
- Utilizar os principais comandos do Git;
- Criar e gerenciar ramificações (*branches*);
- Realizar integração de código utilizando **merge**;
- Aplicar boas práticas no uso do Git em equipes de desenvolvimento.

---

# 1. Controle de Versão

## Definição

**Controle de versão** é um sistema que registra todas as alterações realizadas em arquivos ao longo do tempo, permitindo recuperar versões anteriores, acompanhar modificações e facilitar o trabalho colaborativo.

Em desenvolvimento de software, ele permite que vários desenvolvedores trabalhem simultaneamente no mesmo projeto sem sobrescrever o trabalho uns dos outros.

Além do código-fonte, qualquer arquivo pode ser versionado, como:

- Documentação;
- Scripts;
- Arquivos de configuração;
- Planilhas;
- Projetos de banco de dados.

---

## Exemplo

Imagine um arquivo chamado:

```
Sistema.java
```

Ao longo do projeto ele sofre diversas alterações:

```
Versão 1 → Cadastro
Versão 2 → Login
Versão 3 → Relatórios
Versão 4 → Correção de bugs
Versão 5 → Melhorias
```

Sem um sistema de versionamento seria necessário criar arquivos como:

```
Sistema.java
Sistema_novo.java
Sistema_final.java
Sistema_final2.java
Sistema_final_agora_vai.java
```

Esse tipo de organização torna o projeto confuso e dificulta o trabalho em equipe.

O controle de versão resolve esse problema registrando automaticamente todo o histórico.

---

# 2. Motivação

Entre os principais benefícios do controle de versão estão:

- Histórico completo das alterações;
- Recuperação de versões anteriores;
- Trabalho simultâneo entre vários desenvolvedores;
- Identificação de quem realizou cada alteração;
- Comparação entre versões;
- Facilidade para testar novas funcionalidades;
- Maior segurança contra perda de código;
- Integração com plataformas como GitHub, GitLab e Bitbucket.

---

## Exemplo de cenário

Uma equipe possui quatro desenvolvedores.

```
Ana      → Login
Carlos   → Relatórios
Maria    → API
Pedro    → Correções
```

Sem controle de versão seria muito difícil unir todas essas alterações.

Com Git cada desenvolvedor trabalha em sua própria ramificação e posteriormente integra suas mudanças ao projeto principal.

---

# 3. Sistemas de Controle de Versão

Existem dois modelos principais.

---

## Controle de Versão Centralizado

Nesse modelo existe um único servidor contendo todo o histórico do projeto.

Todos os desenvolvedores acessam esse servidor para enviar e receber alterações.

```
              Servidor

            Projeto Central
                  ▲
      ┌───────────┼───────────┐
      │           │           │
 Desenvolvedor Desenvolvedor Desenvolvedor
       A            B            C
```

### Vantagens

- Administração simples;
- Controle centralizado;
- Histórico único.

### Desvantagens

- Dependência do servidor;
- Se o servidor ficar indisponível, ninguém consegue trabalhar normalmente;
- Maior risco caso o servidor seja perdido.

### Exemplos

- CVS
- Subversion (SVN)

---

# Controle de Versão Distribuído

Cada desenvolvedor possui uma cópia completa do repositório.

Todo o histórico fica armazenado localmente.

```
          Repositório Remoto

                GitHub

             ▲     ▲      ▲

          Git     Git    Git
         Local   Local  Local

          Ana    João   Maria
```

Cada computador possui:

- histórico completo;
- branches;
- commits;
- tags.

É possível trabalhar totalmente offline.

---

## Vantagens

- Maior velocidade;
- Trabalho offline;
- Backup natural;
- Menor risco de perda;
- Melhor suporte ao desenvolvimento colaborativo.

### Exemplos

- Git
- Mercurial

---

# 4. Git

## O que é?

Git é um sistema de controle de versão distribuído criado por **Linus Torvalds**, em 2005, durante o desenvolvimento do kernel Linux.

Seu principal objetivo era oferecer um sistema:

- rápido;
- confiável;
- distribuído;
- seguro;
- eficiente para grandes projetos.

Hoje é o sistema de versionamento mais utilizado no mundo.

---

## Como o Git funciona?

O Git registra "fotografias" (*snapshots*) do projeto.

Cada vez que realizamos um **commit**, é criada uma nova versão do projeto.

```
Commit A

↓

Commit B

↓

Commit C

↓

Commit D
```

Cada commit possui:

- identificador único (hash);
- autor;
- data;
- mensagem;
- alterações realizadas.

---

# Estrutura do Git

```
Working Directory

↓

Staging Area

↓

Repository
```

## Working Directory

Arquivos sendo editados.

## Staging Area

Arquivos preparados para entrar no próximo commit.

## Repository

Histórico permanente do projeto.

---

# Fluxo básico

```
Editar

↓

git add

↓

git commit

↓

git push
```

---

# 5. Comandos Essenciais

## Criar um repositório

```bash
git init
```

---

## Clonar um projeto

```bash
git clone URL_DO_REPOSITORIO
```

Exemplo:

```bash
git clone https://github.com/usuario/projeto.git
```

---

## Verificar o estado

```bash
git status
```

Mostra:

- arquivos modificados;
- novos arquivos;
- arquivos preparados para commit.

---

## Adicionar arquivos

Arquivo específico:

```bash
git add arquivo.java
```

Todos os arquivos:

```bash
git add .
```

---

## Criar um commit

```bash
git commit -m "Implementa cadastro de usuários"
```

A mensagem deve descrever claramente a alteração realizada.

---

## Visualizar histórico

```bash
git log
```

Versão resumida:

```bash
git log --oneline
```

---

## Enviar alterações

```bash
git push
```

---

## Atualizar projeto

```bash
git pull
```

---

## Ver diferenças

```bash
git diff
```

---

## Configurar usuário

```bash
git config --global user.name "Seu Nome"

git config --global user.email "email@exemplo.com"
```

---

# 6. Branches (Ramificações)

## O que é uma Branch?

Uma **branch** é uma linha independente de desenvolvimento.

Ela permite desenvolver novas funcionalidades sem modificar diretamente a versão principal do projeto.

```
main

│

├──────────────

│
├── cadastro
│

├── login
│

└── relatorios
```

Cada desenvolvedor pode trabalhar em uma branch diferente.

---

## Criar uma branch

```bash
git branch cadastro
```

---

## Trocar de branch

```bash
git checkout cadastro
```

Ou utilizando o comando moderno:

```bash
git switch cadastro
```

---

## Criar e trocar

```bash
git checkout -b cadastro
```

ou

```bash
git switch -c cadastro
```

---

## Listar branches

```bash
git branch
```

---

## Remover branch

```bash
git branch -d cadastro
```

---

# Exemplo de fluxo

```
main

↓

Criar branch login

↓

Implementar login

↓

Commit

↓

Merge na main
```

---

# 7. Git Merge

Após concluir uma funcionalidade, é necessário integrá-la à branch principal.

Esse processo é chamado de **merge**.

```
main

│

├───────────────

│
└── login

↓

Merge

↓

main atualizada
```

---

## Como realizar

Trocar para a branch principal:

```bash
git switch main
```

Atualizar a branch:

```bash
git pull
```

Realizar a integração:

```bash
git merge login
```

Enviar ao repositório remoto:

```bash
git push
```

---

## Conflitos

Um conflito ocorre quando duas pessoas alteram a mesma parte de um arquivo.

Exemplo:

Ana altera:

```java
String nome = "Ana";
```

Carlos altera:

```java
String nome = "Carlos";
```

Ao realizar o merge o Git não sabe qual alteração manter.

Nesse caso será necessário resolver o conflito manualmente.

Após corrigir:

```bash
git add .

git commit
```

---

# Fluxo de Trabalho

```text
Criar Branch

↓

Desenvolver

↓

git add

↓

git commit

↓

git push

↓

Pull Request

↓

Code Review

↓

Merge

↓

Deploy
```

---

# 8. Boas Práticas

## Faça commits pequenos

Evite um único commit contendo centenas de alterações.

Prefira:

```
✔ Cadastro concluído

✔ Correção da validação

✔ Ajuste da tela de login
```

---

## Escreva boas mensagens

Ruim:

```
Correções
```

Melhor:

```
Corrige validação do CPF no cadastro
```

---

## Commite frequentemente

Commits menores tornam o histórico mais organizado e facilitam a identificação de problemas.

---

## Nunca desenvolva diretamente na `main`

Crie uma branch para cada funcionalidade.

Exemplo:

```
feature/login

feature/cadastro

feature/pdf

bugfix/email

hotfix/security
```

---

## Atualize sua branch frequentemente

Antes de iniciar novas alterações:

```bash
git pull
```

---

## Resolva conflitos imediatamente

Não deixe conflitos acumularem.

Quanto mais tempo passar, mais difícil será resolvê-los.

---

## Utilize Pull Requests

Antes de integrar uma branch:

- revisão do código;
- testes;
- aprovação da equipe.

Isso aumenta significativamente a qualidade do software.

---

# Resumo

Ao final desta aula, o estudante deve ser capaz de:

- Explicar o conceito de controle de versão;
- Diferenciar sistemas centralizados e distribuídos;
- Compreender o funcionamento do Git;
- Utilizar os principais comandos;
- Criar e gerenciar branches;
- Integrar alterações utilizando `git merge`;
- Resolver conflitos básicos;
- Aplicar boas práticas de versionamento em projetos colaborativos.

---

# Exercícios Propostos

1. Inicialize um novo repositório Git em um diretório vazio.
2. Crie um arquivo `README.md`, adicione-o ao repositório e realize o primeiro commit.
3. Crie uma branch chamada `feature/login` e adicione uma funcionalidade fictícia ao projeto.
4. Retorne para a branch `main` e realize o merge da `feature/login`.
5. Consulte o histórico de commits utilizando `git log --oneline`.
6. Simule um conflito de merge modificando a mesma linha de um arquivo em duas branches diferentes e resolva o conflito manualmente.
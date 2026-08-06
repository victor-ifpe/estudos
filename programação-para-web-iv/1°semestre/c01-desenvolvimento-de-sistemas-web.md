# C01 - Desenvolvimento de Sistemas Web

## Introdução

O **Desenvolvimento de Sistemas Web** consiste na criação de aplicações acessadas por meio de navegadores ou outros clientes conectados à internet. Esses sistemas são amplamente utilizados em diversos contextos, como comércio eletrônico, educação, bancos, redes sociais e sistemas corporativos.

Um sistema web moderno é composto por diferentes camadas que trabalham em conjunto para oferecer uma aplicação segura, eficiente e escalável.

---

# Sistemas Web

Um **sistema web** é uma aplicação executada em um servidor e acessada por meio de um navegador ou aplicativo cliente utilizando a internet ou uma rede interna.

Exemplos de sistemas web:

- Sistemas acadêmicos;
- Lojas virtuais;
- Internet Banking;
- Sistemas de gestão empresarial (ERP);
- Redes sociais;
- Plataformas de streaming.

### Características

- Acesso remoto;
- Não exige instalação (na maioria dos casos);
- Atualização centralizada;
- Compatível com diferentes dispositivos;
- Facilidade de manutenção.

---

# Arquitetura Cliente-Servidor

A arquitetura **Cliente-Servidor** é o modelo mais utilizado no desenvolvimento de sistemas web.

Nela existem dois componentes principais:

## Cliente

O cliente é responsável pela interface com o usuário.

Exemplos:

- Navegador (Chrome, Firefox, Edge);
- Aplicativos Android;
- Aplicativos iOS;
- Aplicações Desktop.

Suas responsabilidades incluem:

- Receber dados do usuário;
- Enviar requisições;
- Exibir respostas.

## Servidor

O servidor executa toda a lógica da aplicação.

Suas responsabilidades incluem:

- Processar requisições;
- Validar informações;
- Consultar bancos de dados;
- Gerar respostas;
- Garantir segurança.

### Fluxo de comunicação

```text
Usuário
   │
   ▼
Cliente (Browser)
   │ HTTP
   ▼
Servidor
   │
Banco de Dados
   │
Servidor
   │ HTTP
   ▼
Cliente
```

---

# Comunicação Cliente-Servidor

A comunicação ocorre através de uma **requisição (Request)** enviada pelo cliente ao servidor.

O servidor processa a solicitação e devolve uma **resposta (Response)**.

Exemplo:

```text
Cliente
   │
   ├── GET /produtos
   │
Servidor
   │
   ├── Consulta banco
   │
   └── Retorna JSON
```

Essa comunicação normalmente utiliza o protocolo HTTP.

---

# Protocolo HTTP

O **HTTP (HyperText Transfer Protocol)** é o protocolo responsável pela comunicação entre clientes e servidores na Web.

É um protocolo baseado no modelo **requisição-resposta**.

## Estrutura da requisição

Uma requisição HTTP possui:

- Método
- URL
- Cabeçalhos (Headers)
- Corpo (Body)

Exemplo:

```http
GET /usuarios HTTP/1.1
Host: exemplo.com
Accept: application/json
```

---

## Métodos HTTP

### GET

Obtém informações.

```http
GET /clientes
```

---

### POST

Cria um novo recurso.

```http
POST /clientes
```

---

### PUT

Atualiza completamente um recurso.

```http
PUT /clientes/10
```

---

### PATCH

Atualiza parcialmente um recurso.

```http
PATCH /clientes/10
```

---

### DELETE

Remove um recurso.

```http
DELETE /clientes/10
```

---

## Códigos de resposta

| Código | Significado |
|---------|-------------|
| 200 | OK |
| 201 | Criado |
| 204 | Sem conteúdo |
| 400 | Requisição inválida |
| 401 | Não autorizado |
| 403 | Proibido |
| 404 | Não encontrado |
| 500 | Erro interno |

---

# APIs REST

## O que é uma API?

API (**Application Programming Interface**) é um conjunto de regras que permite que diferentes sistemas se comuniquem.

Uma API define:

- quais recursos existem;
- como acessá-los;
- quais dados enviar;
- quais dados receber.

---

## O que é REST?

REST (**Representational State Transfer**) é um estilo arquitetural utilizado para construir APIs utilizando HTTP.

Características:

- Comunicação via HTTP;
- Recursos identificados por URLs;
- Stateless (sem estado);
- Uso dos métodos HTTP;
- Respostas normalmente em JSON.

---

## Exemplo de API REST

### Buscar todos os produtos

```http
GET /api/produtos
```

Resposta:

```json
[
    {
        "id":1,
        "nome":"Notebook",
        "preco":3500
    },
    {
        "id":2,
        "nome":"Mouse",
        "preco":80
    }
]
```

---

### Buscar um produto

```http
GET /api/produtos/1
```

---

### Inserir produto

```http
POST /api/produtos
```

Body:

```json
{
    "nome":"Teclado",
    "preco":150
}
```

---

### Atualizar produto

```http
PUT /api/produtos/1
```

---

### Remover produto

```http
DELETE /api/produtos/1
```

---

# JSON

JSON (**JavaScript Object Notation**) é um formato leve para troca de dados entre sistemas.

É atualmente o formato mais utilizado em APIs REST.

## Exemplo

```json
{
    "id":10,
    "nome":"Carlos",
    "idade":25,
    "ativo":true
}
```

Também suporta listas:

```json
[
    {
        "id":1,
        "nome":"Notebook"
    },
    {
        "id":2,
        "nome":"Monitor"
    }
]
```

### Vantagens do JSON

- Leve;
- Fácil leitura;
- Fácil escrita;
- Compatível com praticamente todas as linguagens;
- Excelente desempenho.

---

# Server-Side Rendering (SSR) x Single Page Application (SPA)

## Server-Side Rendering (SSR)

No SSR, o servidor gera toda a página HTML antes de enviá-la ao navegador.

Fluxo:

```text
Cliente
      │
      ▼
Servidor gera HTML
      │
      ▼
HTML pronto
      │
      ▼
Navegador
```

### Vantagens

- Melhor SEO;
- Primeira renderização mais rápida;
- Menor processamento no navegador.

### Desvantagens

- Cada navegação exige nova requisição;
- Maior carga no servidor.

Exemplos:

- Spring MVC + Thymeleaf;
- ASP.NET MVC;
- Django;
- Laravel.

---

## Single Page Application (SPA)

Na SPA existe apenas uma página HTML inicial.

O JavaScript controla toda a navegação.

Fluxo:

```text
Cliente
      │
Carrega aplicação
      │
JavaScript
      │
API REST
      │
Atualiza apenas os dados
```

### Vantagens

- Interface rápida;
- Experiência semelhante à de aplicativos;
- Menor tráfego de páginas completas.

### Desvantagens

- SEO mais complexo;
- Maior processamento no navegador;
- Primeira carga pode ser mais lenta.

Exemplos:

- React;
- Angular;
- Vue.js.

---

## Comparação

| SSR | SPA |
|------|-----|
| HTML gerado no servidor | HTML gerado no navegador |
| Melhor SEO | SEO mais complexo |
| Primeira carga rápida | Navegação muito rápida |
| Mais trabalho do servidor | Mais trabalho do cliente |

---

# Spring Boot

O **Spring Boot** é um framework baseado no ecossistema Spring que facilita a criação de aplicações Java, especialmente APIs REST e microsserviços.

Seu objetivo é reduzir a configuração necessária para iniciar um projeto.

Exemplo de endpoint:

```java
@RestController
@RequestMapping("/produtos")
public class ProdutoController {

    @GetMapping
    public List<String> listar() {
        return List.of("Notebook", "Mouse", "Teclado");
    }

}
```

---

# Vantagens do Spring Boot

- Configuração automática (**Auto Configuration**);
- Servidor embarcado (Tomcat, Jetty ou Undertow);
- Inicialização rápida de projetos;
- Grande produtividade;
- Fácil integração com bancos de dados;
- Suporte nativo para APIs REST;
- Ecossistema robusto;
- Integração com Spring Security, Spring Data JPA e Spring Cloud;
- Ideal para microsserviços.

---

# Spring Boot x Spring MVC

Embora relacionados, Spring Boot e Spring MVC possuem propósitos diferentes.

## Spring MVC

É um framework responsável pela camada web seguindo o padrão **Model-View-Controller (MVC)**.

Ele oferece:

- Controllers;
- Mapeamento de URLs;
- Views (JSP, Thymeleaf);
- Validação;
- Tratamento de requisições HTTP.

Sem Spring Boot, é necessário configurar manualmente diversos componentes.

---

## Spring Boot

O Spring Boot não substitui o Spring MVC; ele o utiliza e simplifica sua configuração.

Ele adiciona recursos como:

- Configuração automática;
- Dependências simplificadas;
- Servidor embarcado;
- Gerenciamento facilitado de projetos;
- Inicialização rápida.

### Comparação

| Spring MVC | Spring Boot |
|-------------|-------------|
| Framework para desenvolvimento web | Framework que simplifica o ecossistema Spring |
| Requer mais configuração | Configuração automática |
| Geralmente necessita de servidor externo | Servidor embarcado |
| Mais complexo para iniciar | Fácil de iniciar |
| Focado na camada web | Abrange toda a aplicação |

**Resumo:** o Spring MVC é responsável pela arquitetura web (Model-View-Controller), enquanto o Spring Boot simplifica a criação e a configuração de aplicações Spring, utilizando o Spring MVC internamente para o desenvolvimento da camada web.
# teste-autenticacao-supabase
# Testes de Autenticação API - Supabase e Postman

## Introdução

Este projeto foi desenvolvido como parte de uma atividade acadêmica sobre testes de caixa cinza em APIs de autenticação.

Foram utilizadas as ferramentas Supabase, Postman Desktop e GitHub para configurar um ambiente de autenticação, executar requisições HTTP e validar o comportamento de uma API de login.

## Objetivo da Atividade

O objetivo desta atividade é compreender o funcionamento de uma API de autenticação e aplicar testes funcionais utilizando a técnica de caixa cinza.

Durante a atividade, foram realizados testes de login com diferentes entradas, verificando os códigos de status HTTP, as respostas JSON e o comportamento do sistema diante de credenciais válidas e inválidas.

## Configuração do Supabase

Foi criado um projeto na plataforma Supabase para disponibilizar o ambiente de autenticação.

A autenticação foi configurada utilizando e-mail e senha, permitindo o cadastro de usuários e a realização de testes de login.

Um usuário de teste foi criado no painel Authentication → Users.

As informações utilizadas para a conexão com a API foram:

- API URL: `[URL do projeto]`
- Tipo de autenticação: E-mail e senha
- Usuário de teste: `[E-mail utilizado]`

A API URL e a chave pública do projeto foram utilizadas para configurar as requisições no Postman.

As credenciais privadas não foram incluídas neste repositório por motivos de segurança.

### Evidências

![Projeto criado no Supabase](prints/01-projeto-supabase.png)

![Usuário criado no Supabase](prints/02-usuario-criado.png)

## Configuração do Postman

Foi criado um Workspace no Postman Desktop com o nome `Testes de Autenticação Supabase`.

Também foi criado um Environment chamado `Supabase - Testes`, contendo as seguintes variáveis:

| Variável | Descrição |
|---|---|
| base_url | URL do projeto Supabase |
| api_key | Chave pública da API |
| email | E-mail do usuário de teste |
| password | Senha do usuário de teste |

As variáveis foram utilizadas para facilitar a reutilização das requisições e evitar a necessidade de preencher manualmente os dados em cada teste.

### Evidências

![Workspace criado no Postman](prints/03-workspace-postman.png)

![Environment configurado](prints/04-variaveis-postman.png)

## Configuração das Requisições

Foi criada uma requisição HTTP utilizando o método POST para realizar a autenticação do usuário.

### Endpoint utilizado

`POST {{base_url}}/auth/v1/token?grant_type=password`

### Headers

| Header | Valor |
|---|---|
| apikey | {{api_key}} |
| Authorization | Bearer {{api_key}} |
| Content-Type | application/json |

### Body JSON

```json
{
  "email": "{{email}}",
  "password": "{{password}}"
}
```

A requisição envia o e-mail e a senha do usuário para o endpoint de autenticação do Supabase.

O objetivo é verificar se as credenciais fornecidas são válidas e se o sistema retorna um token de acesso.

## Execução dos Testes

Foram planejados e executados testes de autenticação utilizando diferentes entradas.

Os testes foram realizados diretamente no Postman Desktop, observando o status HTTP, o conteúdo da resposta JSON e as mensagens retornadas pela API.

### Tabela de Cenários

| Cenário | Entrada utilizada | Resultado esperado | Resultado obtido | Status |
|---|---|---|---|---|
| Login válido | E-mail e senha corretos | HTTP 200 e access token | [Preencher] | [OK/Falha] |
| Senha incorreta | E-mail correto e senha errada | Erro de autenticação | [Preencher] | [OK/Falha] |
| Usuário inexistente | E-mail não cadastrado | Acesso negado | [Preencher] | [OK/Falha] |
| Campos vazios | E-mail e senha vazios | Erro de validação | [Preencher] | [OK/Falha] |
| Credenciais inválidas | Credenciais incorretas | Mensagem de erro | [Preencher] | [OK/Falha] |

### Evidências dos testes

![Teste de login válido](prints/05-login-valido.png)

![Teste de senha incorreta](prints/06-senha-incorreta.png)

![Teste de usuário inexistente](prints/07-usuario-inexistente.png)

![Teste de campos vazios](prints/08-c

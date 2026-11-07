# Testes de Caixa Cinza em API de Autenticação — Supabase e Postman

# 1. Introdução

Este projeto tem como finalidade aplicar testes de caixa cinza em uma API de autenticação utilizando a plataforma Supabase e a ferramenta Postman.

A atividade consiste em configurar um ambiente de autenticação, cadastrar usuários para testes e realizar requisições HTTP para verificar o funcionamento do processo de login.

Os testes contemplam diferentes situações, incluindo credenciais válidas, senhas incorretas, usuários inexistentes e campos vazios.

# 2. Objetivo da Atividade

O objetivo é compreender e aplicar testes de caixa cinza em APIs de autenticação, verificando se o sistema responde corretamente às diferentes entradas fornecidas.

Para isso, foram realizados procedimentos de configuração do Supabase, criação de usuários, configuração do Postman, elaboração de requisições HTTP e validação das respostas retornadas pela API.

Também foi utilizado o recurso de Scripts do Postman para automatizar verificações e facilitar a análise dos resultados.

# 3. Configuração do Supabase

Foi criado um projeto na plataforma Supabase para disponibilizar o ambiente de autenticação utilizado durante os testes.

Após a criação do projeto, foi configurado o provedor de autenticação por e-mail e senha, verificando se a funcionalidade estava habilitada.

Em seguida, foi realizado o cadastro de um usuário de teste por meio da opção Authentication → Users.

Também foram obtidas as credenciais necessárias para comunicação com a API, incluindo a Project URL e a API Key.

Essas configurações permitiram estabelecer o ambiente necessário para realizar as requisições de autenticação.

# 4. Configuração do Postman

Foi utilizado o Postman Desktop para realizar e validar as requisições HTTP.

Inicialmente, foi criado um Workspace para organizar o ambiente de trabalho. Em seguida, foi configurado um Environment contendo as variáveis utilizadas durante os testes.

As variáveis configuradas foram:

- `base_url`: endereço da API do Supabase.
- `api_key`: chave pública da API.
- `email`: e-mail do usuário cadastrado.
- `password`: senha do usuário cadastrado.

Também foi criada uma Collection denominada Testes de Autenticação, responsável por organizar as requisições dos diferentes cenários.

A utilização dessas configurações facilita a reutilização das informações e a organização dos testes.

# 5. Configuração das Requisições

Para realizar a autenticação, foi utilizada uma requisição HTTP com o método POST.

O endpoint utilizado foi:

```http
{{base_url}}/auth/v1/token?grant_type=password
```

A requisição foi configurada com os seguintes Headers:

- `apikey`: chave pública do projeto Supabase.
- `Authorization`: identificação da aplicação por meio da chave pública.
- `Content-Type`: application/json.

No Body da requisição foi utilizado o formato JSON, contendo os campos de e-mail e senha.

Para o login válido, foram utilizadas as variáveis configuradas no Environment:

```json
{
  "email": "{{email}}",
  "password": "{{password}}"
}
```

A finalidade da requisição é enviar as credenciais do usuário para validação no serviço de autenticação do Supabase.

Quando as credenciais são válidas, a API retorna informações da sessão, incluindo o access token. Quando são inválidas, retorna uma mensagem indicando que a autenticação não foi realizada.

# 6. Execução dos Testes

Foram definidos cinco cenários para verificar o comportamento da API diante de diferentes condições de autenticação.

**6.1 Login válido**

Foram utilizadas as credenciais corretas de um usuário previamente cadastrado.

Resultado esperado: autenticação realizada com sucesso, retorno do status HTTP 200 e disponibilização do access token.

**6.2 Senha incorreta**

Foi utilizado o e-mail de um usuário cadastrado, acompanhado de uma senha incorreta.

Resultado esperado: autenticação recusada e retorno de uma mensagem de erro.

**6.3 Usuário inexistente**

Foi utilizado um endereço de e-mail que não possui cadastro no ambiente Supabase.

Resultado esperado: acesso negado e retorno de uma mensagem de erro de autenticação.

**6.4 Campos vazios**

Foram enviados os campos de e-mail e senha sem preenchimento.

Resultado esperado: rejeição da requisição e retorno de uma resposta indicando a ausência de dados necessários para autenticação.

**6.5 Credenciais inválidas**

Foram utilizadas informações incorretas para simular uma tentativa de autenticação inválida.

Resultado esperado: autenticação recusada e retorno de uma mensagem de erro.

**Validação automatizada**

Foram utilizados Scripts do Postman para verificar os códigos de resposta HTTP e a presença de informações esperadas no JSON retornado pela API.

Também foi utilizado o Collection Runner para executar os testes organizados na Collection, permitindo analisar os resultados das validações realizadas.

# 7. Registro dos Testes

Os testes realizados foram documentados em uma planilha específica, contendo a identificação de cada cenário, as entradas utilizadas, os resultados esperados e os resultados obtidos.

O registro permite acompanhar o comportamento da API, comparar os resultados e identificar possíveis falhas durante a execução.

A documentação dos testes é importante para manter um histórico das validações realizadas e facilitar futuras verificações do funcionamento da autenticação.

# 8. Resultados Obtidos

Nesta etapa são considerados os resultados obtidos durante a execução dos cinco cenários de autenticação.

A análise contempla os códigos de resposta HTTP, os conteúdos retornados em JSON, as mensagens de erro e a disponibilização do access token no cenário de login válido.

Os resultados registrados permitem verificar se a API apresentou o comportamento esperado para cada situação testada.

# 9. Conclusão

A realização desta atividade permitiu compreender e aplicar testes de caixa cinza em uma API de autenticação, utilizando o Supabase como ambiente de autenticação e o Postman para execução e validação das requisições HTTP.

Durante o desenvolvimento, foram configurados os recursos necessários para realizar testes com diferentes condições de autenticação, verificando o comportamento da API diante de credenciais válidas e inválidas.

A utilização do Postman possibilitou analisar os códigos de resposta HTTP, os dados retornados em JSON e as mensagens de erro. Além disso, os Scripts e o Collection Runner permitiram automatizar parte das verificações.

A atividade também demonstrou a importância da documentação dos testes, permitindo registrar os procedimentos realizados e identificar possíveis falhas.

Por fim, os testes de caixa cinza são importantes para verificar o funcionamento de APIs, pois permitem analisar o comportamento do sistema considerando informações sobre sua estrutura, endpoints, parâmetros e respostas.

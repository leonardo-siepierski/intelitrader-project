# HTTP Protocol

O protocolo HTTP (Hypertext Transfer Protocol) é responsável pela comunicação cliente-servidor, onde o cliente é o navegador e o servidor pode estar na nuvem ou fisicamente alocado. Ele é responsável por trazer as informações do servidor, que é solicitada através do *request* (pedido) pelo navegador, e é enviado pelo servidor através da *response* (resposta).

## HTTP Methods

Para que essa comunicação ocorra de forma estruturada, existem os métodos HTTP, em que cada um é responsável por uma função específica.

### GET

O método GET é utilizado quando o objetivo é apenas recuperar dados. Por exemplo, buscar um usuário no banco de dados, ou conferir um pedido que já foi realizado.

### POST

O método POST tem a função de enviar dados, o que efetivamente causa uma alteração no servidor (diferentemente do método GET). Algumas das funções desse método são cadastrar um novo usuário, criar um novo pedido ou adicionar uma reportagem a um portal de notícias.

### PUT

O método PUT altera informações no servidor, assim como o método POST, mas é utilizado para editar a representação de uma informação. O conteúdo a ser modificado pelo POST é enviado através do *body* do request. Pode ser usado para editar um usuário já existente, ou alterar uma postagem feita em uma rede social.

### PATCH

Similar ao PUT, o método PATCH tem como função alterar informações existentes, mas é utilizado para alterar *parcialmente* um conteúdo. Ou seja, ao invés de enviar todas as informações da entidade a ser alterada no *body*, apenas envia as informações a serem alteradas.

### DELETE

O método DELETE é utilizado quando é necessário deletar um recurso. Pode ser usado para remover um usuário de um banco de dados, uma postagem de rede social, etc.

### HEAD

O HEAD é similar ao GET, com a diferença de que o método HEAD apenas solicita os headers, sem o body.

### TRACE

O método TRACE serve para retornar o input realizado para o usuário, o que o torna útil para debugging.

### OPTIONS

O método OPTIONS solicita as opções de comunicação permitidas em um determinado servidor ou URL.

### CONNECT

O método CONNECT serve para iniciar uma comunicação de duas vias através de um servidor proxy.

## HTTP headers

Os headers permitem que a comunicação entre o cliente e o servidor possa passar informações adicionais, tanto no request quanto na response.

#### Authorization

O request header *authorization* traz as credenciais necessárias para autenticar o acesso do usuário ao servidor, garantindo acesso a um recurso protegido.

#### Content-Type

Em um request, o header *content-type* indica o tipo do conteúdo da recurso, antes dele sofrer alguma mudança (criptografia, por exemplo).

Quando utilizado em uma response, traz ao cliente o conteúdo real do conteúdo retornado.

```
content-type: application/javascript; charset=utf-8
```

### Cookie

Contém os cookies armazenados que são associados ao servidor.

```
Cookie: PHPSESSID=298zf09hf012fh2; csrftoken=u32t4o3tb3gg43; _gat=1
```

#### Host

Serve para especificar o host e o número da porta do servidor para onde foi feita a requisição. Caso não seja especificada, é implicitamente a porta padrão (443 para HTTPS e 80 para HTTP).

#### Referer

O header *referer* contém o endereço parcial ou absoluto da página que fez a requisição. Ele é utilizado para indicar a página de onde os usuários estão visitando.

## Response Codes

Ainda para que exista uma padronização entre diferentes desenvolvedores, foram criados os response codes. Eles servem para representar o que aconteceu: se a requisição retornou algum conteúdo, se houve algum problema interno, se houve algum problema na soliitação, etc.

Eles são agrupados da seguinte forma:

### 1xx - Informational

#### 100 - Continue
Esse código quer dizer que a requisição inicial foi aceita e deve prosseguir

### 2xx - Success

#### 200 - OK
Significa que a requisição foi bem sucedida. É utilizada quando o método GET retorna a informação solicitada, por exemplo

#### 201 - Created
Significa que a requisição criou com sucesso um recurso (por exemplo, um método POST que cria um usuário no banco)

#### 204 - No Content
O servidor realizou a requisição, mas não tem um conteúdo a ser retornado. Pode ser utilizado quando o método DELETE é realizado com sucesso
### 3xx - Redirection

#### 304 - Not Modified
Foi feita uma requisição GET, mas o documento não foi modificado - ou seja, não existe a necessidade de retransmitir as informações. É um redirecionamento implícito a uma informação cacheada

### 4xx - Client error

#### 400 - Bad Request
Quer dizer que a solicitação não pôde ser interpretada pelo servidor devido a um problema de sintaxe na requisição

#### 401 - Unauthorized
A requisição foi feita sem a devida autenticação do usuário. Pode ser que as credenciais não tenham sido fornecidas ou que estejam incorretas

#### 403 - Forbidden
Significa que a requisição não pode ser executada, mesmo que as credenciais sejam fornecidas. Pode ser devido a um tempo máximo ter sido ultrapassado, por exemplo

#### 404 - Not Found
O erro 404 quer dizer que o servidor não encontrou uma correspondência ao serviço requisitado pelo cliente. Pode significar que o endereço foi digitado incorretamente, ou que foi modificado

#### 409 - Conflict
Esse código quer dizer que existe um conflito entre as informações do servidor e as informações da requisição. Por exemplo, uma tentativa de cadastro de usuário com um email que já existe no banco de dados, sendo que deve ser único

### 5xx - Server error

#### 500 - Internal Server Error
É uma forma genérica de indicar um erro no servidor
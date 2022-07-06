# Protocolo HTTP

O protocolo HTTP (Hypertext Transfer Protocol) é responsável pela comunicação cliente-servidor, onde o cliente é o navegador e o servidor pode estar na nuvem ou fisicamente alocado. Ele é responsável por trazer as informações do servidor, que é solicitada através do *request* (pedido) pelo navegador, e é enviado pelo servidor através da *response* (resposta).

## Métodos HTTP

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
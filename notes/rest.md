# REST
- REST: Representational State Transfer (Transferência de estado representacional).
- SOAP é protocolo e REST é arquitetura.
- REST precisa apenas de HTTP, SOAP exige extensões.
- Estado Representacional: Informações que a aplicações tem no momento.
- Mensagens através de JSON ou XML
- Uso de convenções de verbos, status e URIs

## API Restful

Quando falamos em arquitetura REST, temos que entender como será disponibilizado o recurso para o consumo externo. Não existe um padrão para ser seguido. Podemos organizar a API de várias formas, mas sempre fazendo prevalecer o bom senso. Quando falamos que existe um bom senso, estamos falando que existem formas que são mais aceitáveis que outras, além de muito mais intuitivas.

Vejam as estruturas abaixo:
```
www.myapp.com/api/vendas/clientes

www.api.myapp.com/vendas/clientes

www.api.myapp.com/v1/vendas/clientes
```

Observem que, em primeiro lugar, precisamos de um domínio para acessar a API. Em nosso exemplo, temos dois modelos:
```
www.myapp.com/api/
www.api.myapp.com/
```

Ambos são utilizados, basta escolher o que mais se encaixar no projeto.

Em seguida, temos vendas, que é o nome da API. Alguns desenvolvedores não utilizam o nome, quando se trata de uma API pequena, é interessante utilizar. Vamos supor que desenvolveremos um ERP. Disponibilizaremos uma API para RH, outra para estoque, outra para financeiro e etc. Será interessante nomear as APIs, para ficar mais intuitivo e organizado.

Por último, temos clientes, que é o recurso acessado e disponibilizado, externamente, para os usuários. Esta é a parte mais importante da API. Neste exemplo estamos disponibilizando um recurso de clientes para as aplicações. Através deste recurso, permitimos que as aplicações externas consultem, atualizem, adicionem ou removam clientes. Resumindo, podemos falar que o recurso permite que os usuários manipulem a regra de negócio da API.
Entendendo API RESTful

Quando se fala em API RESTful, muitas vezes, geram dúvidas em relação ao conceito ou significado.
- Sigla: Descrição
- API: Interface de programação
- REST: Arquitetura que foi descrita acima
- ful: Implementação completa da arquitetura

Em resumo, quando falamos RESTful estamos falando da implementação da arquitetura REST em nossa API.
Alguns dos verbos http mais importantes

|  Verbo HTTP |           Descrição            | Segurança  |         Rota         |
|:-----------:|--------------------------------|------------|----------------------|
|     GET     | Consultar informações          | Seguro     | GET /clientes        |
|    POST     | Criar um novo recurso          | Não seguro | POST /pedidos        |
|     PUT     | Atualizar um recurso existente | Não seguro | PUT /pedidos/2320    |
|   DELETE    | Excluir um recurso existente   | Não seguro | DELETE /pedidos/4060 |
|   OPTIONS   |	Consultar informações na API   | Seguro     | OPTIONS /clientes    |

Quando falamos sobre requisição ser segura ou não, não estamos falando sobre autenticação, ou verificando se o usuário tem ou não permissão para fazer tal ação. Estamos falando que a requisição irá ou não modificar o estado da aplicação. O get é seguro porque ele não altera nada em nossos dados, apenas, retorna resultados.

Os outros verbos são considerados não seguros porque eles irão modificar dados na API. Qualquer mudança externa, é considerada não segura, para API.

Notem que no PUT e no DELETE, identificamos qual elemento deverá ser modificado ou excluído da API, através da url. Estamos passando o ID do item que deverá sofrer alteração ou remoção. Existem alguns casos em que o desenvolvedor programa para que o PUT, caso não seja encontrado o ID de atualização, trabalhe como um POST e crie o elemento que não existe. Este procedimento não está errado, desde que seja utilizado de forma correta e inteligente.

O mesmo ocorre quando mandamos uma requisição do tipo POST, para criarmos um elemento, mas o elemento já existe. A API deve reconhecer e atualizar o item, ao invés de criar um novo. Vocês encontrarão muitos recursos deste tipo.

Temos os verbos específicos para cada ação, mas isso não impede, de forma inteligente, que utilizemos um verbo para executar outra ação. Lembrando que este procedimento deve estar na regra de negócio da API.

Vale a pena falarmos que a Rota, ou URI, pode ser maior do que as presentes na tabela acima. Podemos, além de editar um item, querer alterar algum subitem e para isso, deveremos identificá-lo na URI. Desta forma, a URI pode ficar maior, de acordo com a nossa necessidade.

Os verbos mais utilizados são: GET, POST, PUT e DELETE. Existe o OPTIONS, que muitos vezes é esquecido, que é reponsável por trazer informação da API e o que ela nos disponibiliza.

No exemplo acima, estamos mandando um OPTIONS para clientes. Esta requisição informará quais tipos de verbos poderemos enviar para a API. Se, para o recurso clientes estivesse , apenas, o envio de GET e POST, saberíamos que não adiantaria enviar um PUT, por exemplo.

Utilizamos OPTIONS, também, para informar quais headers podemos passar em nossa requisição. Suponham que queiram utilizar um Content Type, na requisição, basta passar um OPTIONS para a API e ela retornará se é possível ou não. De acordo com o retorno, executaremos ou não, determinada ação.
Conclusão

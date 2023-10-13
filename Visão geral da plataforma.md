# Visão geral da plataforma
A plataforma de desenvolvedor da API de SMS da Zenvia fornece tudo o que desenvolvedores precisam para começar a usar nossa API e realizar disparos de SMS para todas as operadoras.

Os guias aqui disponibilizados concedem ferramentas, recursos, dados e produtos de API para você efetuar disparos de mensagens em grande volume.

## Por que usar nossas APIs?

A API SMS da Zenvia permite realizar envios em grandes volumes e receber mensagens SMS por meio de uma API REST. Ao todo, temos 6 (seis) endpoints, sendo eles:

-   Enviar SMS único;
    
-   Enviar varios SMS simultaneamente;
    
-   Consultar status do SMS;
    
-   Listar novos SMS recebidos;
    
-   Consultar SMS recebidos por período;
    
-   Cancelar SMS agendado.

### Requisitos de uso

Antes de utilizar a API de SMS, é necessário criar a sua conta para receber via e-mail a sua credencial, ou seja, login e senha de integração.

Para iniciar, recomendamos a leitura do artigo disponível em nossa Central de ajuda: [API de SMS: Criar conta e receber credenciais para integração](https://zenvia.movidesk.com/kb/pt-br/article/427526/02-api-de-sms-criar-conta-e-receber-credenciais-para-integracao?preview=true&revisionId=1720271&versionId=2753)

### Autenticação
Para utilizar a API SMS da Zenvia o usuário deve realizar uma autenticação básica através da inclusão de um cabeçalho HTTP.

Para tanto, o procedimento para autenticar é o abaixo descrito:
  
1.  Utilizar a string `conta:senha`
    
2.  Concatenar em uma codificação base64
    
3.  Incluir a codificação em um `Authorization: Basic cabeçalho HTTP` conforme o exemplo: `Authorization: Basic Y29udGE6c2VuaGE=`

> :bulb: O valor após a palavra `Basic` é uma chave Base64 da sua conta e senha.

Para obter este valor, há duas maneiras:

1.  Utilizar o comando base64 no linux: `$ echo -n conta:senha | base64` `Y29udGE6c2VuaGE=`
2. Codificar gratuitamente no site [base64Encode](https://www.base64encode.org/)

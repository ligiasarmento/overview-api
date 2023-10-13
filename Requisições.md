# Requisições
As APIs de SMS da Zenvia são baseadas no padrão REST e formato JSON para receber e retornar os dados.

Os recursos disponíveis são acessados através de solicitações HTTP por meio do seguinte caminho:

### Cabeçalhos

Os dados de autenticação retornados na etapa **Requisitos de uso** são o ticket de acesso para os serviços disponíveis nas nossas APIs.

Eles serão validados sempre que uma requisição for feita e todas devem incluir, além do cabeçalho de autenticação, os seguintes headers:

| Código| Descrição
| :--- | :--- |
| `Content-Type`|application/json
| `Accept`|application/json
| `Cache-Control`|no-cache

### Parâmetros

Recomendamos a utilização do parâmetro id. Ele serve como um identificador único de sua mensagem em nossa plataforma e pode ser utilizado para consulta de status ou mesmo para evitar envios duplicados.

Caso você queira enviar um Flash SMS, nossa API possui um parâmetro opcional para indicar que a mensagem deve ser enviada como um Flash SMS.

Para exibir essa funcionalidade, o parâmetro poderá ser informado tanto no envio único como no envio para vários destinatários e deve conter um valor do tipo `boolean`.

> :bulb: Para este tipo de envio, é necessário entrar em contato com nosso atendimento e solicitar que sua conta seja habilitada para Flash SMS.

| Parâmetro| Valor
| :--- | :--- |
| `flashSMS`|**True**: Flash SMS
| `flashSMS`|**False**: SMS normal

#### Shortcodes

Para contas que possuam múltiplos short codes dedicados, é possível selecionar o short code que será utilizado no envio da mensagem através do parâmetro opcional sender. Para mais informações sobre a utilização, consulte a equipe de suporte.

### Métodos

Os métodos utilizados nas APIs de SMS são POST ou GET e variam de acordo com a função utilizada.

| Endpoint| Método
| :--- | :--- |
| Enviar SMS único | <font color="blue">POST
| Enviar varios SMS simultaneamente| <font color="blue">POST
| Consultar status do SMS| <font color="green">GET
| Listar novos SMS recebidos| <font color="blue">POST
| Consultar SMS recebidos por período| <font color="green">GET
| Cancelar SMS agendado| <font color="blue">POST

### Respostas

Os retornos de chamada de status do SMS permitem receber eventos relacionados aos seus envios por meio de solicitações HTTP.

Você pode configurar um `StatusCallBackURL` tanto para mensagens enviadas quanto para recebidas usando a API REST.

Sempre que um evento ocorrer, será feita uma solicitação HTTP para a URL. As chamadas retornarão quatro tipos de códigos, `status`, `statusMessage`, , `statusDetail` e `statusDetailMessage` e os seguintes eventos de retorno serão gerados:

#### StatusCode

| StatusCode| Descrição (StatusMessage)
| :--- | :--- |
| `00`|Ok
| `01`|Scheduled
| `02`|Sent
| `03`|Delivered
| `04`|Not Received
| `05`|Blocked - No Coverage
| `06`|Blocked - Black listed
| `07`|Blocked - Invalid Number
| `08`|Blocked - Content not allowed
| `08`|Blocked - Message Expired
| `09`|Blocked
| `10`|Error

#### DetailCode

| Code (StatusDetail)| Descrição (StatusDetailMessage)
| :--- | :--- |
| `000`|Message Sent
| `001`|Message Scheduled
| `002`|Message successfully canceled
| `010`|Empty message content
| `011`|Message body invalid
| `012`|Message content overflow
| `013`|Incorrect or incomplete ‘to’ mobile number
| `014`|Empty ‘to’ mobile number
| `015`|Scheduling date invalid or incorrect
| `016`|ID overflow
| `017`|Parameter ‘url’ is invalid or incorrect
| `018`|Field ‘from’ invalid
| `021`|‘id’ fieldismandatory
| `080`|Message with same ID already sent
| `100`|Message Queued
| `110`|Message sent to operator
| `111`|Message confirmation unavailable
| `120`|Message received by mobile
| `130`|Message blocked
| `132`|Message already canceled
| `133`|Message content in analysis
| `134`|Message blocked by forbidden content
| `135`|Aggregate is Invalid or Inactive
| `136`|Message expired
| `140`|Mobile number not covered
| `141`|International sending not allowed
| `145`|Inactive mobile number
| `150`|Message expired in operator
| `160`|Operator network error
| `161`|Message rejected by operator
| `162`|Message cancelled or blocked by operator
| `170`|Bad message
| `171`|Bad number
| `172`|Missing parameter
| `180`|Message ID notfound
| `190`|Unknown error
| `200`|Messages Sent
| `210`|Messages scheduled but Account Limit Reached
| `240`|File empty or not sent
| `241`|File too large
| `242`|File readerror
| `300`|Received messages found
| `301`|No received messages found
| `400`|Entity saved
| `900`|Authentication error
| `901`|Account type not support this operation.
| `990`|Account Limit Reached – Please contact support
| `998`|Wrong operation requested
| `999`|Unknown Error

### Limitações 

A API de SMS oferece recursos em pacotes de serviços para garantir segurança, estabilidade e confiabilidade. Há uma limitação em solicitações, especialmente em conexões HTTP simultâneas acima de 100.

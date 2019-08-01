# Bots

Chat-Bots® es un servicio conversacional de respuesta automática, donde se integran como su nombre lo indica tecnologías de Chats \(plataformas de conversación\) y Bots \(Sistemas de respuestas automáticas\).

Funciona cuando en una conversación un usuario final envía un mensaje al Bot y éste devuelve otro automáticamente en respuesta, siguiendo una serie de reglas de negocio fácilmente definibles mediante sencillos diagramas de flujo.

## Modelo del bot

A dicho conjunto de reglas se le denomina modelo del Bot. El portal de Chat-Bots® ofrece una herramienta llamada [diseñador](https://chat-bots.co/es/docs/technical-issues#designer) donde se puede construir paso a paso el modelo del Bot.

## Estados

Durante una conversación el Bot debe saber en qué punto va, para que las respuestas generadas sean coherentes con el contexto de la conversación. Para ello el Bot utiliza una máquina de estados que determina dicho contexto.

Hay un estado inicial para las conversaciones nuevas y se pueden definir cuantos más estados sean necesarios dependiendo de los temas que el Bot sea capaz de responder. Cada vez que el Bot contesta, puede o no, hacer una transición a un estado diferente dentro de la conversación.

## Variables del bot

Para que el Bot pueda determinar con mayor precisión el contexto de la conversación, además del Estado, se pueden definir una serie de variables que se van poblando durante el transcurso de la conversación. Es posible definir tantas variables como sea necesario dependiendo de las reglas y alcance que se le otorgue al Bot.

## Variables de conversación

Se definen dentro de un objeto llamado `chat` que las contiene y tal cual como se mencionó anteriormente, estas variables se van llenando durante la conversación.

El ámbito de dichas variables se define por cada conversación y el tiempo de vigencia \([timeout del diálogo](https://chat-bots.co/es/docs/technical-issues#)\) de la misma.

## Variables del mensaje

Están definidas dentro de un objeto llamado msg y representan el mensaje enviado por el usuario final al Bot:

Varible

Descripción

`msg.body`

En esta variable aparece el texto del mensaje enviado por el usuario.

`msg.type`

En esta variable aparece tipo del mensaje enviado por el usuario.

`chat` - Si es un mensaje de texto  
`image` - Si el mensaje enviado es una imagen o fotografía.  
`document` - Si el mensaje enviado es un documento PDF, Word, Excel o Powerpoint  
`location` - Si el mensaje enviado es una ubicación GPS.  
`audio` - Si el mensaje enviado es un audio.  
`video` - Si el mensaje enviado es un video.

En caso que el tipo de mensaje enviado sea diferente de chat, en la variable `msg.body` se puede obtener el contenido del elemento multimedia en formato DataUrl.

`msg.id`

En esta variable aparece el identificador del usuario que envía el mensaje

Para el caso de WhatsApp, el identificador es el código del país + el número del teléfono + @c.us.

`msg.profile`

En esta variable aparece el nombre del usuario que envía el mensaje.

Para el caso de WhatsApp, la mayoría de las veces este campo aparecerá en blanco ya que los usuarios cuando instalan WhatsApp no lo suministran.

`msg.email`

En esta variable aparece la dirección de correo electrónico del usuario que envía el mensaje.

No disponible en WhatsApp

`msg.line`

En esta variable aparece el identificador de la línea de WhatsApp o página de Facebook por medio de la cual el Bot interactúa con el usuario final que envía el mensaje.

`msg.platform`

En esta variable aparece el tipo de plataforma de mensajería usada por el Bot.

* WhatsApp
* Facebook Messenger
* Web Chat

_Las variables de mensaje son efímeras y sólo tienen ámbito mientras el Bot determina la respuesta que debe devolver al usuario final._


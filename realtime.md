# State of the Real-time Web with Django

_Speaker: Aymeric Augustin @aymericaugustin_

_Slides: http://static.myks.org/data/20130905-DjangoCon-Real-time_Web.pdf_


The real-time web enables users to retrieve info as soon as it is available
instead of polling for changes.

- Games
- Chat
- Notifications
- Collaboration
- Social feeds
- VoIP

For all these cases the server needs to push information to the browser. HTTP
doesn't work that way with the traditional request/response cycle.

One solution is HTTP long polling, in which the server keeps the request on
hold until it has information to send back. Another is HTTP streaming in
which the server sends a series of events in a single HTTP response by
chuncking the data (?). But HTTP was not designed for bidirectional
communication. These techniques stretch the original semantic of HTTP.

Websockets provide bidirectional communication in the context of the existing
HTTP infrastructure. 

RFC 6455
- opening handshake to upgrade from HTTP
- framing protocol and closing handshake
- provisions for extensions and subprotocols

As of v 10 IE supports websockets. Android does not support them.



## Reference

Speaker on github: aaugustin  
Demo code: https://github.com/aaugustin/dcus13rt  
http://aaugustin.github.io/websockets/  
[PEP 3156 -- Asynchronous IO Support Rebooted](http://www.python.org/dev/peps/pep-3156/)


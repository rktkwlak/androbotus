**Androbotus** is a lightweight framework for developing robots on Android platform (and not only android in future). It's all Java and uses only very basic communication protocols to make it really easy to run on any platform (the lowest Android version tested on is 2.3.6).

There are two main concepts: _Module_ and _MessageBroker_. _Module_ accepts high-level commands and translates it into lower-level commands for other modules or low-level signals for servos and motors.

_MessageBroker_ is just a message broker, which provides communication between modules via Pub/Sub model. A robot software can run on multiple remote server nodes. For this purpose _MessageBroker_ can send and receive remote messages via TCP/UDP protocols.

The project's blog is here: http://androbotus.wordpress.com/
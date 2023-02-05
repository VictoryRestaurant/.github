```mermaid

---
title: System diagramm
---
flowchart LR 

%% ----------------------- Desktop -----------------------

Desktop(((Desktop))) --> DesktopGateway(Desktop Gateway) --> InnerGateway(Inner Gateway)

InnerGateway(Inner Gateway) -- Desktop --> AuthService(Auth Service)

InnerGateway(Inner Gateway) -- Desktop --> UsersService(Users Service)

InnerGateway(Inner Gateway) -- Desktop --> ContactService(Contact Service)

InnerGateway(Inner Gateway) -- Desktop --> FoodService(Food Service)

InnerGateway(Inner Gateway) -- Desktop --> BookingService(Booking Service)

InnerGateway(Inner Gateway) -- Desktop --> SubscribersService(Subscribers Service)

%% ----------------------- Web -----------------------

Web(((Web))) --> WebGateway(Web Gateway) --> InnerGateway(Inner Gateway)

InnerGateway(Inner Gateway) -- Web --> ContactService(Contact Service)

InnerGateway(Inner Gateway) -- Web --> FoodService(Food Service)

InnerGateway(Inner Gateway) -- Web --> BookingService(Booking Service)

InnerGateway(Inner Gateway) -- Web --> SubscribersService(Subscribers Service)

%% ----------------------- Mobile -----------------------

Mobile(((Mobile))) --> MobileGateway(Mobile Gateway) --> InnerGateway(Inner Gateway)

InnerGateway(Inner Gateway) -- Mobile --> FoodService(Food Service)

SubscribersService --> MailSenderService(Mail sender Service)

%% ----------------------- Databases & Broker -----------------------

AuthService --> AuthDb[(Auth Database)]

UsersService --> UsersDb[(Users Database)]

AuthService <-...-> MessageBroker(Message Broker)
MessageBroker(Message Broker) <-...-> AuthDb[(Auth Database)]

UsersService <-...-> MessageBroker(Message Broker)
MessageBroker(Message Broker) <-...-> UsersDb[(Users Database)]

ContactService --> ContactDb[(Contact Database)]

BookingService --> BookingDb[(Booking Database)]

SubscribersService --> SubscribersDb[(Subscribers Database)]

MailSenderService --> MailSenderDb[(Mail sender Database)]

FoodService --> FoodDb[(Food Database)]

MailSenderService <-...-> MessageBroker(Message Broker)
MessageBroker(Message Broker) <-...-> MailSenderDb[(Mail sender Database)]

SubscribersService <-...-> MessageBroker(Message Broker)
MessageBroker(Message Broker) <-...-> SubscribersDb[(Subscribers Database)]

%% ----------------------- Links -----------------------

click FoodService "https://github.com/VictoryRestaurant/VictoryRestaurant.Foods" _blank

click Web "https://github.com/VictoryRestaurant/VictoryRestaurant.Web" _blank
```

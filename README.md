# MASsenger Web API


## Description
MAS is a messenger server, written in C# ASP.NET Core, with a HTTP API.
- It was designed with following qualities in mind:
    - Simplicity
    - Consistency in both API and server code
    - Robustness
- Specifications and behaviors of it were drawn from many publicly specified protocols and messaging platforms, such as:
    - IRC (IRCv3 and Modern IRC specs)
    - XMPP
    - Matrix
    - Telegram
    - Discord
    - Mango

The goal of our system is to successfully send messages from one user, to another user or group.


## Features
- **Text & file message (send & delete)**
- **Bots**
- **Private chat**
- **Group chat**
- **Group role base limit (owner, admin & user)**
- **Group user ban**
- **Avatar for users and group chats**
- **System messages**


## Design
- **User related classes:**
```
User

Session
```

- **Chat related classes:**
```
BaseChat
|
|----> PrivateChat
|                   
\----> GroupChat

PrivateChatUser

GroupChatUser                 
```

- **Message related classes:**
```
Message

FileContent                
```

- **Database diagram:**
  - https://dbdiagram.io/d/MAS-Diagram-693c5ea5e877c63074a588aa


## Build

Assuming you are running debian or alikes, first install dotnet repositories:
```
$ sudo apt install dotnet dotnet-sdk-6.0 sqlite3
```
then clone this repository:
```
$ git clone https://github.com/hjicks/gaweb
$ cd gaweb
$ dotnet build
```


## Tech Stack
- **SDK:** `.NET 6`
- **Framework:** `ASP.NET Core`
- **Architecture:** `Clean`
- **Design patterns:** `Mediator`, `Repository`, `Unit of work`, `Result`, `Option`, `Factory method`
- **Persistence:**
    - DBMS: `SQLite`
    - ORM: `Entity Framework`, `Dapper`
- **Business logic:** `MediatR`, `Fluent Validation`
- **Realtime communication:** `SignalR`
- **Authentication:** `JWT Bearer`
- **Authorization:** `Role based using JWT claims`
- **Logging:** `Serilog`, `Seq`
- **Unit test:** `xUnit`, `Moq`
- **Integration test:** `C# CLI client`
- **External service:** `An internal bot connected to a LLM`
- **API documentation:** `OpenAPI using Swagger`
- **Continuous integration:** `Github Actions`
- **Programming languages:** `C#`, `SQL`	
- **IDE & tools:** `Visual Studio`, `DB Browser for SQLite`, `Postman`, `GNU Emacs`



## Contribution
- **Saeed Mahjoob (@hjicks):**
    - Database design
    - Realtime communication --> `SignalR`
    - Unit test --> `xUnit`, `Moq`
    - Integration test
    - CLI client --> `C# Console App`
    - Continuous integration --> `Github Actions`
    - Several controllers

- **Amir Ali Salimiyan (@Salimiyan):**
    - Validation --> `Fluent Validation`
    - Logging --> `Serilog`, `Seq`
    - Documentation --> `OpenAPI using Swagger`
    - Several controllers

- **Mahdi Hosseini Shahabadi (@mhs04):**
    - ORM, seed, repositories & unit of work --> `Entity Framework`, `Dapper`
    - Business logic --> `With CQRS using MediatR`
    - Result & option classes (pattern)
    - File storage & blob service
    - System message service
    - Authentication --> `JWT Bearer`, `Refresh Token`
    - Authorization --> `Role based using JWT claims`
    - External service --> `An internal bot connected to a LLM using C# Console App`
    - Security --> `Hashing`, `CORS`
    - Exception handling --> `Through Middleware`
    - Multi language error message best practices
    - Several controllers

[Back To Home](/)

# TK-Crypto

TK Crypto is currently a WIP. Please keep an eye on our announcements channel for updates!

## Config

## Server Exports

**Example Export**

```js
global.exports["tk-crypto"].example(); // Demonstration Export
```

## Server Events

**Example Event**

```js
// From Client
emit(`${GetCurrentResourceName()}:server:exampleEvent`, Param1, Param2); // Demonstration Event

// From Server
TriggerServerEvent(`${GetCurrentResourceName()}:server:exampleEvent`, Param1, Param2); // Demonstration Event
```

## Client Exports

```js
global.exports["tk-crypto"].example(); // Demonstration Export
```

## Client Events

**Example Event**

```js
// From Client
emit(`${GetCurrentResourceName()}:server:exampleEvent`, Param1, Param2); // Demonstration Event

// From Server
TriggerClientEvent(`${GetCurrentResourceName()}:server:exampleEvent`, Param1, Param2); // Demonstration Event
```

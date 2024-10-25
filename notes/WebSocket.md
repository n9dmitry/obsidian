
Чтобы создать соединение 
```python
import asyncio
2import websockets
3
4async def echo(websocket, path):
5    while True:
6        message = await websocket.recv()  # Получаем сообщение от клиента
7        print(f"Received: {message}")
8        await websocket.send(f"Echo: {message}")  # Отправляем обратно
9
10start_server = websockets.serve(echo, "localhost", 8765)
11
12asyncio.get_event_loop().run_until_complete(start_server)
13print("Server started on ws://localhost:8765")
14asyncio.get_event_loop().run_forever()
```


```python
import asyncio
2import websockets
3
4async def hello():
5    async with websockets.connect("ws://localhost:8765") as websocket:
6        await websocket.send("Hello, WebSocket!")  # Отправляем сообщение серверу
7        response = await websocket.recv()  # Получаем ответ от сервера
8        print(f"Received from server: {response}")
9
10asyncio.get_event_loop().run_until_complete(hello())
```



[[Python]]
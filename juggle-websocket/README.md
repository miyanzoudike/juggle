# juggle-websocket



# juggle-websocket是一个支持事件派发的websocket客户端


### 特点：


    1、支持事件派发



### 依赖juggle-help，juggle-event


### 快速开始：


    npm install juggle-websocket


### 如何使用：


```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="../juggle-help/dist/juggle-help.js" type="text/javascript"></script>
    <script src="../juggle-event/dist/juggle-event.js" type="text/javascript"></script>
    <script src="../juggle-websocket/dist/juggle-websocket.js" type="text/javascript"></script>
    <script type="text/javascript">
        var websocketClient;
        function onConnect(event) {
            alert("与服务器建立链接，发送消息");
            var data = {
                "wsOpCode": "testc",
                "msg": "你好啊，服务器"
            };
            websocketClient.send(data);
        }
        function onClose(event) {
            alert("与服务器断开链接");
        }
        function onTests(event) {
            var data = event.mData;
            alert("服务器返回" + data.msg);
            websocketClient.close();
        }

        window.onload = function () {
            websocketClient = new juggle.WebSocketClient("ws://localhost:8080/grain-threadwebsocket-test/ws");
            websocketClient.addEventListener(juggle.webSocketEventType.CONNECTED, onConnect, this);
            websocketClient.addEventListener(juggle.webSocketEventType.CLOSE, onClose, this);
            websocketClient.addEventListener(juggle.webSocketEventType.getMessage("tests"), onTests, this);
        }
    </script>
</head>
<body>

</body>
</html>

```

websocket服务器（直接可用）：

https://github.com/dianbaer/grain/tree/master/grain-threadwebsocket-test




	
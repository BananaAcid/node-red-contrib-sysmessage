# node-red-contrib-sysmessage

This module provides a node for Node-RED to quickly show a message at the host system (OSX, Windows).

It is distributed on NPM [node-red-contrib-sysmessage](https://www.npmjs.com/package/node-red-contrib-sysmessage).

## Pre-requisites

This requires Node-RED version 0.14 or more recent.

## Install

Run the following command in your Node-RED user directory (typically `~/.node-red`):

```
npm install node-red-contrib-sysmessage
```

Open your Node-RED instance and you should have the node available in the palette and a new `system` tab in right side panel.

#### Features

It supports OSX and Windows:
- OSX Alert
	- A basic OS message box
- OSX Notification
	- Right hand notification banner, will also be added to the notification center
- OSX Message / iMessage
	- sends messages through the messages.app to any buddy in your list, including iMessages (Hint: add yourself to send to)
- WIN Alert
	- A basic OS message box, at least Win 7
- WIN Notification (will not be added to the notification center)
	- requires POWERSHELL to be available - means at least Win 8 (or earlier with powershell manually installed)
	- does not support a receiver.

#### Note

It is completely based on CLI commands.
The message field supports mustache, using the msg fields.
If no receiver is set, it uses the current host system (not a remote) to show the message.


#### Node Setup

1 in: the payload
1 out [optional]: any console error or message created


#### Example flow

`Button -> alert -> debug out`


Import using the Menu->Import->Clipboard.

```
[{"id":"72013ad3.c27184","type":"sysmessage","z":"2fc3038e.7502e4","command":"osxalert","title":"tit","subtitle":"st","op1":"asd 'fsdf\\n123","op1type":"str","receiver":"","name":"","x":247,"y":260,"wires":[["8c391e4.bfe5be"]]},{"id":"8c391e4.bfe5be","type":"debug","z":"2fc3038e.7502e4","name":"Show debug result","active":true,"console":"true","complete":"payload","x":403,"y":334,"wires":[]},{"id":"c6834579.0edbc","type":"inject","z":"2fc3038e.7502e4","name":"","topic":"","payload":"Button: test it.","payloadType":"str","repeat":"","crontab":"","once":false,"x":154,"y":173,"wires":[["72013ad3.c27184"]]}]
```
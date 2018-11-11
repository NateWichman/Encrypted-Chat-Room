# Encrypted-Chat-Room

Server/Client chat service written in java.

The server allows for multiple clients to join simultaneously by using threads. 

All messages are encrypted with AES encryption. When a client joins, they randomly generate an AES key and send it to the Server. That initial message is encrypted with RSA encryption. For that to happen, the Server will first send its RSA public key to the client. the client will encrypt the AES key with the Server's public key and send the message. The Server will use its RSA private key to decrypt the client's AES key. At this point the client and the Server share the same AES key. All further messages will be encrypted with that AES key.

When the client joins, they will be prompted to choose a username. Any time they send a message from then on, all other clients will see their message in the format "username: message".

The client is able to:
    .Broadcast messages to all other users in the chatroom (default)
    .Send private messages to a specific user (/whisper username msg)
    .View a list of all connected users (/list)
    .Kick users with an administrator password (/kick username )
    .Leave the chatroom (by typing "Exit")

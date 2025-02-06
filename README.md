# Chat en Java - Cliente y Servidor

Este proyecto es una aplicación de chat en **Java** con arquitectura cliente-servidor. Permite que varios clientes se conecten a un servidor y puedan intercambiar mensajes en tiempo real.

---

## 🛠️ Tecnologías utilizadas
- **Java SE**
- **Sockets TCP** para la comunicación cliente-servidor
- **Multithreading** para manejar múltiples clientes simultáneamente

---

## 🗒️ Estructura del proyecto

```
JavaClientChat-main/
│── ChatClient/        # Cliente del chat
│   ├── src/chatclient/
│   │   ├── ChatClient.java  # Lógica del cliente
│   ├── build/classes/chatclient/  # Archivos compilados del cliente
│
│── ChatServer/        # Servidor del chat
│   ├── src/chatserver/
│   │   ├── ChatServer.java  # Lógica del servidor
│   ├── build/classes/chatserver/  # Archivos compilados del servidor
│
│── README.md          # Documento actual
```

---

## 💡 Cómo ejecutar el chat en Linux

### **1. Iniciar el Servidor**
Abre una terminal y navega a la carpeta del servidor:
```bash
cd ~/Escritorio/JavaClientChat-main/ChatServer/build/classes
java chatserver.ChatServer
```
Si el servidor inicia correctamente, deberías ver:
```
Servidor de chat iniciado en el puerto 9876
```

### **2. Conectar Clientes**
Abre **otra terminal** y navega a la carpeta del cliente:
```bash
cd ~/Escritorio/JavaClientChat-main/ChatClient/build/classes
java chatclient.ChatClient
```
Deberías ver:
```
Conectado al servidor en localhost:9876
Bienvenido al chat.
Ingresa tu nombre de usuario:
```
Ingresa un nombre de usuario y presiona **Enter**.

Para abrir más clientes, repite este paso en otras terminales.

### **3. Probar la comunicación**
Si en un cliente escribes:
```
Hola, ¿quién está ahí?
```
En los otros clientes conectados debería aparecer:
```
[usuario1]: Hola, ¿quién está ahí?
```

### **4. Cerrar el servidor y clientes**
- Para cerrar un **cliente**, usa `Ctrl + C` en la terminal.
- Para cerrar el **servidor**, ve a la terminal donde está corriendo y presiona `Ctrl + C`.

---

## 💡 Explicación del Código

### **Servidor (`ChatServer.java`)**
- Escucha conexiones en el puerto **9876**.
- Acepta múltiples clientes usando **hilos (`Thread`)**.
- Mantiene una lista de clientes conectados y reenvía los mensajes a todos menos al remitente (**broadcast**).
- Cuando un cliente se desconecta, se elimina de la lista y se informa a los demás usuarios.

### **Cliente (`ChatClient.java`)**
- Se conecta al servidor en `localhost:9876`.
- Solicita un nombre de usuario y envía mensajes al servidor.
- Recibe mensajes en un hilo separado para no bloquear la entrada del usuario.

---

## 👨‍💻 Autores
- **[Unai Perez Toscano]**  👤

---




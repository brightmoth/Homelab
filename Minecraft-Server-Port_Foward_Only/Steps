# Fabric Minecraft Server with Docker

## 1. Create the server

Install Docker with Docker Compose, then make a folder for the server. In that folder, create `compose.yaml`:

```yaml
services:
  minecraft:
    image: itzg/minecraft-server
    container_name: fabric-server
    ports:
      - "25565:25565"
    environment:
      EULA: "TRUE"
      TYPE: "FABRIC"
      VERSION: "26.3"
      MEMORY: "4G"
      MODRINTH_PROJECTS: |
        fabric-api
    volumes:
      - ./data:/data
    restart: unless-stopped
    stdin_open: true
    tty: true
```

Use a Minecraft version supported by your mods and Fabric API. Back up `data` before changing versions.

## 2. Start the server

Open a terminal in the folder containing `compose.yaml`, then run:

```bash
docker compose up -d
```

Check that it started:

```bash
docker compose logs -f
```

Server files and the world are stored in the `data` folder.

## 3. Port forward for friends

In your router, add a port-forwarding rule:

- **Local IP:** the server computer’s local IPv4 address, e.g. `192.168.1.51`
- **Local port:** `25565` to `25565`
- **Protocol:** TCP
- **Remote IP/port:** leave blank if the router allows it

On Windows, find the local IPv4 address with `ipconfig`; on macOS, check **System Settings → Network**. Reserve that address in the router so it stays the same. Allow TCP port `25565` through the computer’s firewall.

Friends connect using your **public IPv4 address**, which you can find by searching “what is my IP.” They enter it as the server address in Minecraft Java; add `:25565` if needed. Share it only with people you trust.

## 4. Basic commands

Stop the server:

```bash
docker compose down
```

Add mods: stop the server, put compatible server-side `.jar` mod files in `data/mods`, then start it again:

```bash
docker compose up -d
```

Use mods that match the server’s Minecraft version and Fabric loader. Players generally need compatible mods on their clients too.

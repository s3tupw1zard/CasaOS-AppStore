# Pelican Panel

Pelican Panel is an open-source, web-based application designed for easy management of game servers. It offers a user-friendly interface for deploying, configuring, and managing servers, with features like real-time resource monitoring, Docker container isolation, and extensive customization options. Ideal for both individual gamers and hosting companies, it simplifies server administration without requiring deep technical knowledge.

Fly High, Game On: Pelican's pledge for unrivaled game servers.

## Links

* [Website](https://pelican.dev)
* [Docs](https://pelican.dev/docs)
* [Discord](https://discord.gg/pelican-panel)
* [Wings](https://github.com/pelican-dev/wings)

## Supported Games and Servers

Pelican supports a wide variety of games by utilizing Docker containers to isolate each instance.
This gives you the power to run game servers without bloating machines with a host of additional dependencies.

Some of our popular eggs include:

| Category                                                             | Eggs            |               |                    |                |
|----------------------------------------------------------------------|-----------------|---------------|--------------------|----------------|
| [Minecraft](https://github.com/pelican-eggs/minecraft)               | Paper           | Sponge        | Bungeecord         | Waterfall      |
| [SteamCMD](https://github.com/pelican-eggs/steamcmd)                 | 7 Days to Die   | ARK: Survival | Arma 3             | Counter Strike |
|                                                                      | DayZ            | Enshrouded    | Left 4 Dead        | Palworld       |
|                                                                      | Project Zomboid | Satisfactory  | Sons of the Forest | Starbound      |
| [Standalone Games](https://github.com/pelican-eggs/games-standalone) | Among Us        | Factorio      | FTL                | GTA            |
|                                                                      | Kerbal Space    | Mindustry     | Rimworld           | Terraria       |
| [Discord Bots](https://github.com/pelican-eggs/chatbots)             | Redbot          | JMusicBot     | JMusicBot          | Dynamica       |
| [Voice Servers](https://github.com/pelican-eggs/voice)               | Mumble          | Teamspeak     | Lavalink           |                |
| [Software](https://github.com/pelican-eggs/software)                 | Elasticsearch   | Gitea         | Grafana            | RabbitMQ       |
| [Programming](https://github.com/pelican-eggs/generic)               | Node.js         | Python        | Java               | C#             |
| [Databases](https://github.com/pelican-eggs/database)                | Redis           | MariaDB       | PostgreSQL         | MongoDB        |
| [Storage](https://github.com/pelican-eggs/storage)                   | S3              | SFTP Share    |                    |                |
| [Monitoring](https://github.com/pelican-eggs/monitoring)             | Prometheus      | Loki          |                    |                |


## IMPORTANT INSTALLATION INSTRUCTIONS

To use Pelican Panel with e.g. Nginx Proxy Manager in front of it, you need to create the following volume and place a Caddyfile in it:

```
/DATA/AppData/pelican-panel/caddy:/etc/caddy
```

Then in your appdata folder under pelican-panel/caddy you need to create the Caddyfile with the following content:

```
{
    admin off
    email {$ADMIN_EMAIL}
}

:80 {
    root * /var/www/html/public
    encode gzip

    php_fastcgi 127.0.0.1:9000
    file_server
}
```

With this custom configuration, your panel will be bound to port 80 without a ssl cert inside your container.

Then you should only need to set the Scheme to http (without an s), Forward Hostname / IP to `pelican-panel` and the Port to 80.


Now you can access your newly installed panel. And don't forget to run the installer (https://pelican.yourdomain.com/installer)

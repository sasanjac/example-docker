## Konfigurationen

### Docker Secrets

- als `root` Ordner `secrets` anlegen
- darin folgende Dateien erzeugen:
  - `cloudflare_api_key`
  - `cloudflare_email`
  - `authelia_jwt_secret`
  - `authelia_session_secret`
- in Dateien ausschließlich das jeweilige Secret speichern
- viele Docker Images unterstützen Secrets als Environment Variablen: `VARIABLE_FILE: /run/secrets/variable`

### Traefik
- `acme.json` muss erzeugt werden (`touch acme.json`)
- `$DOMAINNAME` in `middlewares.yml` ersetzen

### Pihole

- Hostsystem ggf. nach Anleitung auf Pihole-Website konfigurieren
- lokale Domains in Pihole konfigurieren (z.B `pi.hole`, `fritz.box` usw.), sowie `$DOMAINNAME` auf lokale IP setzen (Zugriff über lokale Verbindung wenn mit Heimnetzwerk verbunden)

### Netatalk

- `$USER` in `afp.conf` ersetzen
- Für Zugriff aus Internet Port 548 weiterleiten

### Samba

- User in `docker-compose.yml` konfigurieren
- Für Zugriff aus Internet Ports 137, 138, 139 und 445 weiterleiten (nicht empfohlen)

### Authelia

- `$DOMAINNAME` in `configuration.yml` ersetzen. OTP Passwort wird bei der ersten Anmeldung in `notification.txt` gespeichert (man kann auch einen Emailserver aufsetzen)
- Benutzer in `users_database.yml` konfigurieren, alternativ LDAP aufsetzen

### Watchtower

- Telegram BotFather aufsetzen und entsprechende Variablen setzen oder Notification über Telegram deaktivieren
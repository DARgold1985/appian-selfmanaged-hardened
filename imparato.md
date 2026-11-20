## 2026-11-06 — DNS
- Risoluzione: resolver -> root -> TLD -> autoritativo; risposta in cache per il TTL
- A = IPv4, AAAA = IPv6, CNAME = alias di un nome, MX = posta (priorità bassa = preferita), TXT = verifiche e SPF
- Il dominio radice non può essere CNAME -> su AWS si usa Alias (gratis, segue gli IP del load balancer)
- Migrazione: abbassare il TTL almeno un TTL prima
- Route 53: failover = DR con health check; weighted = percentuali (canary); latency = regione più veloce
- Diagnosi: DNS -> rete -> porta -> TLS -> applicazione
## 2026-11-20 — HTTP e nginx
- HTTP: richiesta (metodo, percorso, header) e risposta (codice di stato); header Date sempre in GMT
- 502 = l'applicazione dietro il proxy non risponde; 504 = risponde troppo lentamente
- nginx: siti in sites-available, attivati con un collegamento in sites-enabled
- sempre nginx -t prima del reload; errori in /var/log/nginx/error.log (cercare "upstream")
- X-Forwarded-For / X-Forwarded-Proto: l'applicazione vede IP e protocollo reali dell'utente
- listen 80 + listen [::]:80 per IPv4 e IPv6
## 2026-11-02
- Linux: useradd -m, passwd, su vs su -, passwd -l/-u, chage, usermod -aG (mai -G senza -a), userdel -r
- Permessi: rwx, 644/755/600; ~/.ssh 700, chiave privata 600
- Python: due punti e indentazione a 4 spazi definiscono i blocchi
- Python: return per portare un valore fuori da una funzione (scope)
- Python: dati annidati utente["address"]["city"]; f-string con {graffe}
- Git: un comando è finito solo quando ricompare il prompt $
## 2026-11-20 — IAM e Python
- Ruolo = credenziali temporanee via STS; trust policy (chi lo assume) + permission policy (cosa fa)
- Deny esplicito > Allow > implicit deny; i permessi di più policy si sommano
- SCP limita gli account, permission boundary limita una identità (delega), trust policy = chi assume
- s3:ListBucket sull'ARN del bucket, s3:GetObject su bucket/*
- Python: = assegna, == confronta; ':' dopo if/else/for/def; mai Tab, solo spazi (nano -E)
- Un testo si scorre carattere per carattere: normalizzare in lista prima di usarlo
- Traceback si legge dal basso: tipo di errore, poi riga, poi chi l'ha chiamata
- L'indentazione decide quando una riga viene eseguita: dentro l'if, dentro il for, dopo il for

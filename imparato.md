## 2026-11-06 — DNS
- Risoluzione: resolver -> root -> TLD -> autoritativo; risposta in cache per il TTL
- A = IPv4, AAAA = IPv6, CNAME = alias di un nome, MX = posta (priorità bassa = preferita), TXT = verifiche e SPF
- Il dominio radice non può essere CNAME -> su AWS si usa Alias (gratis, segue gli IP del load balancer)
- Migrazione: abbassare il TTL almeno un TTL prima
- Route 53: failover = DR con health check; weighted = percentuali (canary); latency = regione più veloce
- Diagnosi: DNS -> rete -> porta -> TLS -> applicazione
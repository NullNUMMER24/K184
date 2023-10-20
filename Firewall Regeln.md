# Aufgabe 1
Notiert euch in einer Tabelle, was wir sicher schon kennen:

| Aus welchem Netz/NIC | Protokolle L3 + L4 | Quelle (Source) IP/Netz     | Quelle Port(s) (meist any hier OK) | Ziel Port | Bemerkung |
| -------------------- | ------------------ | --------------------------- | ---------------------------------- | --------- | --------- |
| LAN                  | IPv4 + TCP         | LAN-Net (oder nur Admin-PC) | *                                  | 8080      | PRTG      |
| LAN                  | IPv4 + UDP         | DC-Server SV-01             | *                                  | 53        | DNS          |

# Aufgabe 2
## Terminal
1. Via SSH auf die Firewall verbinden
  ```
  ssh root@192.168.110.1
  ```
2. Den Traffic auf dem Interface **"lan0"** analysieren
  ```
  tcpdump -i vmx1 > log
  ```
## Web UI
1. Auf https://192.168.120.1 verbinden
2. Auf `Interfaces` --> `Diagnostics` --> `Packet Capture` clicken
3. Hier kann nun eingestellt werden, auf welchen Interfaces die Packages gesammelt werden. 
4. Domain-Member Server starten (Win-Server in DMZ)
5. Mit Domain Admin anmelden (Welcome$00)
6. Die Datei herunterladen
7. Wireshark öffnen
8. Datei importieren
9. Nach `ldap` suchen

## LDAP Ports

| Nummer | Name | Source IP      | Destination IP | Souce Port | Destination Port |
| ------ | ---- | -------------- | -------------- | ---------- | ---------------- |
| 1      | LDAP | 192.168.120.51 | 192.168.110.50 | 49667      | 389              |
| 2      | LDAP | 192.168.110.50 | 192.168.120.51 | 389        | 49667            |
| 3      | LDAP | 192.168.120.51 | 192.168.110.50 | 49674      | 389              |
| 4      | LDAP | 192.168.110.50 | 192.168.120.51 | 389        | 49674            | 

# Relevante Ports
## LAN --> WAN

| Protokoll   | Port |
| ----------- | ---- |
| HTTPS       | 443  |
| HTTP        | 80   |
| DNS         | 53   |
| SMTP        | 25   |
| Secure SMTP | 587  |
| POP         | 43   |
| IMAP        | 110  |
| ICMP        | 933  | 

## DMZ --> WAN
| Protokoll | Port |
| --------- | ---- |
| HTTP      | 80   |
| HTTPS     | 443  | 

## WAN --> DMZ

| Protokoll | Port |
| --------- | ---- |
| HTTP      | 80   |
| HTTPS     | 443  | 

## LAN --> DMZ

| Protokoll | Port |
| --------- | ---- |
| HTTP      | 80   |
| HTTPS     | 443  |
| RDP       |      |
| SSH       | 22   | 
## DMZ --> LAN

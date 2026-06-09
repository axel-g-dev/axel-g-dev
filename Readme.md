## About Me :
French IT Student, i'm currently learning :<br>- Python<br>- Cybersecurity<br>- Networks <br><br>

## GitHub Stats :

<!-- [![TryHackMe Badge](https://tryhackme-badges.s3.amazonaws.com/axel.g.png)](https://tryhackme.com/p/axel.g) -->

[![GitHub Streak](https://streak-stats.demolab.com?user=axel-g-dev&theme=dark&hide_border=true)](https://git.io/streak-stats)



```mermaid
sequenceDiagram
    autonumber
    participant Capteur
    participant Passerelle
    participant ChirpStack
    participant Mosquitto
    participant Backend
    participant PostgreSQL
    participant Grafana

    Capteur->>Passerelle: Trame LoRaWAN
    Passerelle->>ChirpStack: Paquet UDP (port 1700)
    activate ChirpStack
    Note over ChirpStack: Décodage payload (codec JS)
    ChirpStack->>Mosquitto: PUBLISH JSON (topic/up)
    deactivate ChirpStack
    activate Mosquitto
    Mosquitto->>Backend: SUBSCRIBE topic/up
    deactivate Mosquitto
    activate Backend
    Backend->>PostgreSQL: INSERT INTO mesures
    deactivate Backend
    Grafana->>PostgreSQL: SELECT (requête SQL)
    PostgreSQL-->>Grafana: Résultats
    Note over Grafana: Affichage courbes temps réel
```

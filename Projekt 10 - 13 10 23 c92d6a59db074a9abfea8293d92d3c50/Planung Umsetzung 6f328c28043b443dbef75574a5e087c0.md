# Planung /  Umsetzung

| https://johannesloetzsch.github.io/LF10b/planen.html#welche-systemeigenschaften-sollen-vom-monitoring-%C3%BCberwacht-werden-beschreibe-die-architektur-des-gew%C3%A4hlten-monitoring-setups-am-besten-mit-einer-grafik | Monitoring der CPU, Netwerk und vorallem speicherauslastung überwachen. Monitoring durch Proxmox der VM, Monitoring durch Grafana in einer Cluster VM |  |
| --- | --- | --- |
| https://johannesloetzsch.github.io/LF10b/planen.html#habt-ihr-bereits-gedanken-wie-eine-sp%C3%A4tere-automatisierung-umgesetzt-werden-kann | Proxmox VM Automatisierung
+
Docker CT |  |
| https://johannesloetzsch.github.io/LF10b/planen.html#plant-einen-groben-zeitplan-f%C3%BCr-die-umsetzung | Proxmox VE 1h
Steam Cache Server 2h
Monitoring, Backup, etc  3h |  |
| https://johannesloetzsch.github.io/LF10b/planen.html#wer-aus-dem-team-wird-welche-aufgaben-%C3%BCbernehmen | Flexibel aufteilbar, meist kollektiv zusammarbeiten |  |
| https://johannesloetzsch.github.io/LF10b/planen.html#welche-anleitungen-bzw-tutorials-wollt-ihr-nutzen-welche-sonstige-dokumentation-k%C3%B6nnte-n%C3%BCtzlich-sein | https://linustechtips.com/topic/962655-steam-caching-tutorial/
https://www.tecmint.com/nload-monitor-linux-network-traffic-bandwidth-usage/
https://forum.proxmox.com/threads/how-to-backup-proxmox-configuration-files.67789/ |  |
| https://johannesloetzsch.github.io/LF10b/planen.html#welche-recovery-time-objective-rto-und-recovery-point-objective-rpo-wollt-ihr-erreichen-w%C3%A4hlt-eine-backupstrategie-und-begr%C3%BCndet-die-entscheidung | Cache Server RTO 8 Stunden RPO von config 1 Woche; Proxmox VE die Backups von Proxmox und deren Configs RTO 2 Stunden, RPO 1 |  |
| https://johannesloetzsch.github.io/LF10b/planen.html#beschreibe-deineuer-projekt-selbstdefinierte-aufgabenstellung | Proxmox VE —> Steam Cache Server |  |
| https://johannesloetzsch.github.io/LF10b/planen.html#erstellt-eine-grobe-%C3%9Cbersicht-wie-die-architektur-des-projekes-aussehen-sollen | Proxmox VE, Grafana, Docker,Proxmox Backup, Server im Raum 248 |  |
|  |  |  |
| Mögliche Backupstrategien | restic | proxmox ve |
| * Vollbackup | ja | ja |
| * Inkrementell | ja | ja |
| * Differenziell | nein | ja |
| Mögliche Sicherungsziele | local, sftp, rest, s3, … | local, bacula server |
| Verschlüsselung | ja, symmetisch, mit AES-256 und scrypt [3,4] | ja |
| Prüfsummen + Signaturen | ja, mit message authentication code [4] | ja |
| Softwarelizenz | BSD 2 | GPL |
| Anschaffungskosten | 0€ | 0€ |
| … | … | … |
|  | Grafana [0] + Prometheus [1] | Grafana [2] + influxDB + Proxmox |
| Nötige Komponenten |  |  |
| * Check-Plugins / Exporter | Prometheus-Exporter [4] | nope |
| * Datenbank | Prometheus time series database [5] | influxDB |
| * Dashboard | Grafana Dashboard [6] | Grafana |
| * Notifications | Grafana Alertmanager (builtin) [7] | Grafana |
| Wie/Wo werden Checks ausgeführt? | von Prometheus-Exportern [4] | Proxmox |
| Welche Komponente triggert Checks? | Prometheus-Exporter [4] | VM oder System components |
| Wo werden Daten gespeichert? | Prometheus time series database [5] | influxdb |
| Wo/Wann werden Daten ausgewertet? | im Grafana Dashboard [6] | Grafana oder Proxmox |
| Softwarelizenz | Apache License v2.0 & AGPLv3 [8,9] | Opensource |
| Anschaffungskosten | 0€ | 0€ |
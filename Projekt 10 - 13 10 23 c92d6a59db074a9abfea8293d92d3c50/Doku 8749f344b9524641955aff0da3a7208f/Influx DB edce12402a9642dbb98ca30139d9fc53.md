# Influx DB

Influx DB unter Linux aufsetzen:

1. Öffnen Sie die Befehlszeile.
2. Führen Sie den Befehl `sudo apt update` aus, um das Paketrepository zu aktualisieren.
3. Führen Sie den Befehl `sudo apt install influxdb` aus, um Influx DB zu installieren.
4. Starten Sie den Influx DB-Dienst mit dem Befehl `sudo systemctl start influxdb`.
5. Überprüfen Sie den Status von Influx DB mit dem Befehl `sudo systemctl status influxdb`.
6. Um den Influx DB-Dienst automatisch beim Start des Systems zu starten, verwenden Sie den Befehl `sudo systemctl enable influxdb`.
7. Sie können nun Influx DB verwenden, um Datenbanken und Messungen zu erstellen und abzufragen.

Dann nach belieben konfigurieren

Welche Daten sollen an den NDT gesendet werden für die Live Sync?

Statische Daten ?

Dynamische Daten?

**relativ statisch:**

- Topologie

- Switches/Router

- Interfaces

- Link-Kapazitäten

- Konfiguration

**dynamisch:**

- Traffic

- Utilization

- Queue Depth

- Packet Loss

- Interface State

- Delay

- CPU

- Counter



Benötigt man den latest state? 

wenn ja wie macht man das weil wenn man alles in ein topic haut gibt es keinen weg den latest stand zu ziehen weil latest heißt einfach nur die letzte inbound message. 

Daher die frage wäre ein State Builder usefull? Der baut aus den Messages ein current State zusammen. 

| Variante                  | Umsetzung? / IDee                                                     | version                               |
| ------------------------- | --------------------------------------------------------------------- | ------------------------------------- |
| **NDT hält State selbst** | NDT liest Live-Events und aktualisiert seinen internen State          | **V1**                                |
| **Compacted State Topic** | Kafka enthält pro Key langfristig den letzten bekannten Wert          | für schnellen Wiederanlauf            |
| **State Builder**         | eigener Consumer berechnet State und schreibt ihn ins compacted Topic | Erst nötig, wenn State komplexer wird |




Topic Structure

```text
net.<domain>.<entity>
```

- net.telemetry.v1
	- key=SW01
		- event_type=device.cpu
		- event_type=device.temperature
		- event_type=device.memory
	- key=SW01|xe-001
		- event_type=interface.oper_status
		- event_type=interface.in_octets
		- event_type=interface.out_octets
		- event_type=interface.errors
	- key=SW02|xe-004
		- event_type=interface.oper_status
		- event_type=interface.in_octets



Topic:
net.telemetry

Key:
SW01

Header:
event_type = device.cpu

Payload:
{
  "device_id": "SW01",
  "value": 42,
  "timestamp": "..."
}
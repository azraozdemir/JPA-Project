# JPA-Project

## GymFlow – Fitnessstudio-Verwaltung

## Features

- Mitglied werden (Tarif wählen, Vertrag anlegen)
- Kursplan mit freien Plätzen anzeigen
- Zu einem Kurstermin an- und abmelden
- Offene Zahlungen pro Mitglied anzeigen
- Auswertung: Mitglieder ohne Kursbesuch im aktuellen Monat

## Datenmodell

| Entity | Beschreibung |
|---|---|
| `Person` | Abstrakte Basisklasse für Member und Trainer |
| `Member` | Mitglied des Studios |
| `Trainer` | Leitet Kurstermine |
| `MembershipPlan` | Tarif, z.B. Basic oder Premium |
| `Contract` | Vertrag zwischen Mitglied und Tarif |
| `Payment` | Zahlung zu einem Vertrag |
| `Course` | Kursart, z.B. Yoga oder Spinning |
| `CourseSession` | Konkreter Kurstermin mit Trainer und Raum |
| `Room` | Raum im Studio |
| `Enrollment` | Anmeldung eines Mitglieds zu einem Kurstermin |

### Verwendete JPA-Features

- **Vererbung:** `Person` → `Member` / `Trainer`
- **Master/Detail:** `Contract` → `Payment`
- **Composite Key:** `Enrollment` mit `(member_id, session_id)`
- **Komplexe Queries:** `GROUP BY` / `HAVING`, Aggregatfunktionen, `LEFT JOIN`

## Tech Stack

- Java 21
- Quarkus
- Hibernate ORM (JPA) mit Panache
- PostgreSQL
- JUnit 5 & RestAssured

## Architektur

```
resource   → REST-Endpoints
service    → Geschäftslogik
repository → Datenbankzugriff
entity     → JPA-Entities
dto        → Datenobjekte für die REST-API
```

## Projekt starten

Voraussetzungen: Java 21, Maven, Docker (für die Datenbank über Quarkus Dev Services)

```bash
./mvnw quarkus:dev
```

Die API läuft dann unter `http://localhost:8080`.
Die Dev UI ist unter `http://localhost:8080/q/dev` erreichbar.

### Tests ausführen

```bash
./mvnw test
```

## Team

- David   
- Azra
- Lena

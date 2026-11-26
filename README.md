# De taal Kotlin 2.4 leren

📖 **Lees de tutorial: [https://stahe.github.io/nl-kotlin-oct-2026/](https://stahe.github.io/nl-kotlin-oct-2026/)**

Deze cursus leert u de taal [Kotlin](https://kotlinlang.org/) 2.4 **aan de hand van voorbeelden**: meer dan tweehonderd programma's (337 Kotlin-bestanden), regel voor regel toegelicht, met hun uitvoerresultaten erbij. Hij begint met de basis van de taal en behandelt coroutines, databasetoegang met JDBC en Hibernate, netwerkprogrammering en webservices met Spring Boot.

Dit is de Kotlin-versie van de cursus [De taal Java 25 leren](https://stahe.github.io/nl-java-oct-2026/) (oktober 2026), die zelf een port is van de cursus [C# 14](https://stahe.github.io/nl-csharp-oct-2026/) – een herschrijving van een C#-cursus uit 2008: dezelfde opzet, dezelfde voorbeelden, dezelfde rode draad, maar geschreven in het Kotlin van vandaag. Alle programma's compileren **zonder fouten of waarschuwingen** met Kotlin 2.4.20 (waarschuwingen behandeld als fouten) en zijn uitgevoerd op JDK 25; de in de cursus weergegeven resultaten zijn die van deze uitvoeringen.

| Cursus Java 25 (2026) | Cursus Kotlin 2.4 (2026) |
|---|---|
| Java 25 (LTS), JDK 25 | Kotlin 2.4.20, JDK 25 |
| compacte bronbestanden (`java Prog.java`) | `main`-functies op hoog niveau, `kotlinc`, groene driehoek van IntelliJ IDEA |
| Maven-projecten (`pom.xml`) | Gradle-projecten in Kotlin DSL (`build.gradle.kts`), Gradle 9.8 wrapper |
| `null`, wrapperklassen en `Optional` | `null`-veiligheid in het typesysteem (`?.`, `?:`, `!!`) |
| accessors, records, geen operator-overloading | properties, dataklassen, operator-overloading, extensiefuncties |
| gecontroleerde exceptions, `try` met resources | alleen ongecontroleerde exceptions, `use` |
| Stream API | collectiebewerkingen, sequences |
| functionele interfaces, lambda's | functietypen, lambda's, `inline`-functies, gedelegeerde properties |
| `CompletableFuture`, virtuele threads | **coroutines**: `suspend`, `launch` / `async`, gestructureerde concurrency, `Flow`, `Channel` |
| JUnit 6, Spring Framework 7 | JUnit 6 en `kotlin.test`, Spring Framework 7 (plug-in `kotlin-spring`) |
| Jackson 3 | Jackson 3 met dataklassen |
| JDBC, MySQL Connector/J, HikariCP | hetzelfde, met Kotlin-idiomen |
| Hibernate 7 | Hibernate 7 met de plug-ins `kotlin-jpa` (no-arg) en all-open |
| `HttpClient`, `Socket` / `ServerSocket` | dezelfde klassen, in Kotlin |
| Spring Boot 4 | Spring Boot 4 in Kotlin |

## Opzet van de cursus

| Hoofdstuk | Inhoud |
|---|---|
| Installatie | JDK 25, IntelliJ IDEA / VS Code, de compiler `kotlinc`, Gradle (wrapper, Kotlin DSL), multimoduleprojecten |
| Basis van de taal | typen, `val` / `var`, typeinferentie, stringtemplates, rauwe strings, `null`-veiligheid, conversies, arrays, operatoren, `when`, bereiken en lussen, exceptions, `use`, enums, standaard- en benoemde parameters, lokale functies, `Pair` en destructuring |
| Klassen, interfaces, dataklassen | primaire constructors, properties, `object` en `companion object`, overerving, sealed classes, operator-overloading, indexers, value classes, extensiefuncties, interfaces, abstracte klassen, generics en variantie, packages, dataklassen, smart casts |
| Veelgebruikte Kotlin-klassen | strings, arrays, alleen-lezen en muteerbare collecties, functionele bewerkingen, **sequences**, tekst- en binaire bestanden, JSON met Jackson 3, reguliere expressies (`Regex`) |
| Gelaagde architecturen | [DAO] / [bedrijfslogica] / [UI], Gradle-builds met meerdere projecten, unittests met **JUnit 6** en `kotlin.test`, **dependency injection** met Spring |
| Functietypen, lambda's en gebeurtenissen | functietypen, lambda's, functiereferenties, `fun interface`, closures, compositie, `inline`-functies, listeners, observeerbare gedelegeerde properties |
| Uitvoeringsthreads | `thread { }`, **virtuele threads**, `synchronized`, `@Volatile`, `ReentrantLock`, `Condition`, atomaire bewerkingen, semaforen, concurrente collecties, `ExecutorService`, fork/join, `ThreadLocal`, `ScopedValue` |
| Asynchroon programmeren | **coroutines**: `suspend`-functies, `runBlocking`, `launch`, `async` / `await`, dispatchers, gestructureerde concurrency, exceptions, annulering en time-outs, `Flow`, `Channel`, `CompletableDeferred`, beperkte parallelliteit, coroutines en virtuele threads |
| Databasetoegang met JDBC | MySQL, MySQL Connector/J, `DataSource` en HikariCP, geparametriseerde query's en SQL-injectie, transacties, batches, JDBC met virtuele threads en coroutines |
| **Hibernate** | Kotlin-entiteiten, `SessionFactory` / `Session`, CRUD, HQL en Criteria API, relaties, migraties, optimistische concurrency, native SQL, Spring ORM en `@Transactional` |
| Webprogrammeren | TCP/IP, IPv6, TCP-clients en -servers (één virtuele thread per client), HTTP, `HttpClient`, SMTP met Jakarta Mail |
| Webservices | REST / JSON met **Spring Boot 4** in Kotlin, Kotlin-consoleclients, JavaScript-webclient, Node.js-client |

## De rode draad: een belastingcalculator in 9 versies

Gedurende de hele cursus bouwen we, versie na versie, een applicatie voor het **berekenen van de inkomstenbelasting**:

- **Versie 1**: één enkel programma; **versie 2**: klassen en interfaces; **versie 3**: gegevens gelezen uit een tekst- of JSON-bestand;
- **versies 4 en 5**: een gelaagde architectuur, ingedeeld in Gradle-subprojecten, getest met JUnit en geïntegreerd via dependency injection met Spring;
- **versies 6 en 7**: gegevens opgeslagen in een MySQL-database, opgehaald met JDBC en daarna met Hibernate;
- **versie 8**: een TCP-server voor de belastingberekening en zijn client;
- **versie 9**: een REST-webservice met Spring Boot, zijn consoleclient en zijn webclient.

## Technologieën

Kotlin 2.4.20 · JDK 25 · Gradle 9.8 (Kotlin DSL) · IntelliJ IDEA · kotlinx.coroutines 1.11 · JUnit 6 · Spring Framework 7 · Jackson 3 · MySQL 8 · MySQL Connector/J 9 · HikariCP · Hibernate ORM 7.4 · Jakarta Persistence 3.2 · Spring Boot 4.1 · Laragon

## Vereisten

- Eerdere programmeerervaring in een willekeurige taal.
- Een [JDK 25](https://adoptium.net) (Eclipse Temurin of een andere distributie) en [IntelliJ IDEA](https://www.jetbrains.com/idea/) (Kotlin is ingebouwd). Gradle hoeft niet te worden geïnstalleerd: elke hoofdstukmap bevat zijn eigen wrapper (`gradlew`). Als JDK 25 niet is geïnstalleerd, downloadt Gradle deze automatisch (met de plug-in `foojay-resolver-convention`). [Laragon](https://laragon.org) voor MySQL (hoofdstukken over databases). Installatie-instructies staan in de cursus.

## Auteur

Deze cursus en de bijbehorende code zijn geschreven door **Claude**, de AI van [Anthropic](https://www.anthropic.com) (oktober 2026), in opdracht van **Serge Tahé**, op basis van zijn Java 25-cursus.

Nagelezen door: [Serge Tahé](https://stahe.github.io)

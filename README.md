# IT Home Lab — Windows Server och Active Directory

Det här är **mitt eget IT-labb**. Jag har arbetat med Windows Server, Active Directory och virtuella klienter i VMware. Här visar jag vad jag faktiskt har byggt, hur jag hanterat problem och vad jag lärde mig. Jag använder projektet som en del av min portfölj när jag söker jobb inom IT-support.

## Det jag har gjort

| Teknik | Min erfarenhet | Dokumentation |
|---|---|---|
| Windows Server 2025 | Jag installerade servern i VMware. | [Min AD-labbrapport](01_Active_Directory/README.md) med skärmbilder |
| Active Directory | Jag installerade AD DS och konfigurerade en domänkontrollant för `lab.local`. | [Min AD-labbrapport](01_Active_Directory/README.md) |
| Nätverk | Jag konfigurerade en statisk IP-adress (`10.0.0.1`) på servern. | [Skärmbilder och labbrapport](01_Active_Directory/README.md) |
| Felsökning | Jag löste ett fel i förutsättningskontrollen när servern skulle bli domänkontrollant. | [Min felsökning](01_Active_Directory/README.md#ett-fel-jag-felsökte) |
| Windows 11 i VMware | Jag installerade tidigare en Windows 11-klient under mina Active Directory-övningar. | [Min sammanfattning](02_IT_Support/README.md); bilder från det momentet saknas här |
| DNS, DHCP och klienttester | Jag arbetade tidigare med dessa moment i samband med mina Active Directory-övningar. | [Min sammanfattning](02_IT_Support/README.md); detaljerade testloggar saknas här |

Jag skiljer på det jag har **dokumenterat med skärmbilder** och de praktiska moment jag har **genomfört tidigare men ännu inte dokumenterat i detta repository**. Jag påstår inte att jag har arbetat med riktiga kundärenden bara för att jag gjort övningar.

## Ett konkret problem jag löste

När jag installerade Active Directory Domain Services och skulle konfigurera servern som domänkontrollant stoppades jag av ett fel under förutsättningskontrollen.

Jag granskade felmeddelandet och upptäckte att administratörskontot saknade lösenord. Jag rättade kontots inställning och genomförde sedan konfigurationen. Efteråt kunde jag öppna **Active Directory Users and Computers** och se domänen `lab.local`.

Jag sparade skärmbilder från både felet och den färdiga installationen. Det är ett exempel jag kan visa och förklara under en IT-intervju.

![Min Windows Server-miljö](01_Active_Directory/01-dashboard.png)
![Problemet under AD-konfigurationen](01_Active_Directory/11-prerequisites-check-error.png)
![Active Directory efter installationen](01_Active_Directory/13-aduc-done.png)

## Mina labbrapporter

- [**Active Directory – installation, konfiguration och felsökning**](01_Active_Directory/README.md)
- [**Windows 11, DNS, DHCP och klienttester – tidigare praktiska övningar**](02_IT_Support/README.md)
- [**Så beskriver jag min erfarenhet under en intervju**](02_IT_Support/INTERVIEW_STORIES.md)
- [**Projektbeskrivning för CV och LinkedIn**](02_IT_Support/FOR_EMPLOYERS.md)

## Om erfarenheten

Det här är praktisk **projekt- och labberfarenhet**, inte en anställning som IT-supporttekniker. Jag beskriver bara genomförda moment och skiljer mellan egna dokumenterade resultat och arbete jag behöver komplettera med mer bevis.

**Säkerhet:** Ett lösenordsexempel från en äldre version av projektet har tagits bort från den aktuella dokumentationen. Om lösenordet fortfarande används i labbet måste det bytas eftersom äldre Git-versioner kan innehålla det.

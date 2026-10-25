# IT Home Lab — Windows Server & IT Support

**Praktiskt hemlabb för junior IT-support / helpdesk / onsite IT-tekniker.**

Jag bygger och dokumenterar ett virtualiserat företagsnät i VMware med Windows Server 2025, Active Directory och Windows-klienter. Syftet är att visa **vad jag faktiskt har gjort**, **hur jag felsöker** och **hur jag verifierar lösningar**.

> **Ärlig projektstatus (25 oktober 2026):** Lab 01 har en dokumenterad installation av Windows Server 2025, statisk IPv4-adress och en Active Directory-domänkontrollant. Lab 02 innehåller en installationsplan och sex **simulerade** supportärenden; dessa är ännu inte verifierade som genomförda.

## Projektöversikt

| Del | Innehåll | Status |
|---|---|---|
| [01 — Active Directory](01_Active_Directory/) | Windows Server 2025, VMware, statisk IPv4 (`10.0.0.1`), AD DS-domän `lab.local` | Dokumenterat med skärmbilder |
| [02 — IT-support / First Line](02_IT_Support/README.md) | Windows 11-klient, isolerat labbnät, DNS/DHCP, gruppbehörigheter, GPO |
| [Supportärenden](02_IT_Support/TICKETS.md) | Sex scenarier från inloggning till onboarding | Scenarier klara; tester återstår |
| [Progress / bevis](02_IT_Support/PROGRESS.md) | Status, testresultat, bilder och återstående arbete | Löpande |
| [Arbetsgivarvy](02_IT_Support/FOR_EMPLOYERS.md) | Verifierbara CV- och intervjuformuleringar | Klart utifrån befintlig dokumentation |

## Så är labbet tänkt att fungera

**Planerad isolerad VMware-miljö:**

- **Server:** Windows Server 2025, Active Directory Domain Services, DNS och senare DHCP.
- **Domän:** `lab.local` (befintlig).
- **IP-adresser:** `10.0.0.1` på servern; planerat isolerat `10.0.0.0/24`-nät, klient via DHCP när konfigurerat.
- **Klient:** Windows 11 Enterprise Evaluation, `LAB-PC01`.
- **Fiktiva användare:** Emma (Support), Noah (Ekonomi) och Sara (HR).
- **Träningsmoment:** kontoåtkomst, klientanslutning, nätverksfelsökning, filrättigheter, GPO och nyanställda.

Ingen företagsdata eller riktiga kundärenden ingår.

## Lab 01 — dokumenterad grund

### Det jag gjorde
1. Installerade Windows Server 2025 i VMware.
2. Konfigurerade en statisk IPv4-adress (`10.0.0.1`).
3. Installerade rollen Active Directory Domain Services.
4. Promoterade servern till domänkontrollant för `lab.local`.
5. Dokumenterade ett förutsättningsfel under installationen och hur jag rättade det.

### Ett verkligt felsökningsmoment

Under förutsättningskontrollen för domänkontrollanten upptäcktes att det lokala administratörskontot saknade lösenord. Jag satte ett lösenord på kontot och slutförde konfigurationen.

**Säkerhetsnotering:** Ett äldre README-exempel visade ett konkret labblösenord. Det har tagits bort från den aktuella texten. Lösenord som funnits i Git-historiken eller skärmbilder ska betraktas som exponerade och bytas innan systemet används igen.

### Dokumenterade skärmbilder
![Server Manager](01_Active_Directory/01-dashboard.png)
![Statisk IP-konfiguration](01_Active_Directory/01.1-static-ip.png)
![Förutsättningsfel](01_Active_Directory/11-prerequisites-check-error.png)
![Felsökning](01_Active_Directory/11.1-prerequisites-check-error.png)
![Active Directory Users and Computers](01_Active_Directory/13-aduc-done.png)

## Lab 02 — praktiskt supportarbete

**[Starta här: installera och bygg labbet](02_IT_Support/SETUP.md)**

Därefter arbetar jag med [sex simulerade supportärenden](02_IT_Support/TICKETS.md), dokumenterar varje test med [ärendemallen](02_IT_Support/TICKET_TEMPLATE.md) och uppdaterar den [verifierade statusloggen](02_IT_Support/PROGRESS.md).

> **För rekryterare:** Detta är självständiga teknikprojekt, inte tidigare anställningar eller påhittade kunduppdrag. Endast verifierade labbresultat markeras som slutförda.

## Kompetenser som projektet övar

Windows Server · VMware · Active Directory · DNS · DHCP · Windows 11 · TCP/IP · felsökning · behörigheter · Group Policy · teknisk dokumentation.

**Kontakt och övriga projekt:** [GitHub-profil](https://github.com/Mattan-a11y).

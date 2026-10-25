# Lab 02 — Simulerad IT-support / First Line

> **Status: Under uppbyggnad.** Detta är en plan för praktiska övningar, inte bevis på att ärendena har lösts. Uppdatera `PROGRESS.md` och lägg in egna skärmbilder när du har testat varje moment.

## Syfte
Utöka det befintliga Windows Server 2025-labbet till en liten, realistisk supportmiljö. Öva användarhantering, Windows 11-klienter, domäninloggning, DNS/DHCP, grupprinciper, delade mappar och strukturerad ärendehantering.

**Målroll:** Junior IT-support / First Line / Onsite IT-tekniker.

### Befintlig grund, enligt Lab 01
- VMware med Windows Server 2025.
- Domänkontrollant och Active Directory: `lab.local`.
- Statisk server-IP: `10.0.0.1`.
- Befintliga skärmbilder under `../01_Active_Directory/`.

Vi **återanvänder** detta. Ändra inte domännamnet eller serverns IP utan särskild anledning.

## Föreslagen miljö

| Del | Funktion | Status |
|---|---|---|
| Server-VM: befintligt namn | Windows Server 2025, AD DS | Dokumenterad i Lab 01 |
| Windows 11-klient: LAB-PC01 | Inloggning, grupprinciper, support | Planerad |
| DNS på servern | Domänuppslagning | Ska verifieras |
| DHCP på servern | IP-adresser till klienter | Planerad/behöver verifieras |
| 3 fiktiva användare och 2 grupper | Onboarding och behörigheter | Planerat |
| Gemensam mapp | Behörighetsärenden | Planerad |
| 6 supportärenden | Felsökning och dokumentation | Ej genomförda |

### Nätverk
- En särskild **isolerad** VMware VMnet, inte bridged mot hemmets fysiska nätverk.
- IP-nät: `10.0.0.0/24` (förutsatt att det matchar befintlig server).
- Server/DNS: `10.0.0.1`.
- Exempel på DHCP-intervall: `10.0.0.100–10.0.0.150`.
- DNS till Windows-klienten: **10.0.0.1**, inte en extern DNS.
- Om nätverket är helt isolerat och saknar router: lämna standardgateway tom. Internet fungerar då inte från klienten, vilket är okej för domänövningarna.

**Viktigt:** Kontrollera först att VMware själv eller värddatorn inte använder `10.0.0.1` på samma virtuella nät, att VMware DHCP inte delar ut adresser och att serverns DHCP aldrig kopplas till hemmets vanliga LAN.

### Kapacitet
Rimlig start: värddator med omkring 16 GB RAM eller mer och tillräckligt med ledigt diskutrymme; server-VM cirka 4 GB RAM, klient-VM cirka 4 GB RAM. Anpassa efter datorns faktiska resurser. Windows 11 kräver kompatibel virtuell hårdvara, bland annat TPM 2.0.

## Vad en rekryterare ska kunna granska
1. **Arkitektur** — en enkel beskrivning av miljön och varför nätet isolerats.
2. **Konfiguration** — bilder av domänanslutning, OU, användare, DHCP, DNS och GPO.
3. **Ärenden** — problem → analys → åtgärd → verifiering.
4. **Reflektion** — vad som först gick fel och varför den slutliga lösningen fungerade.

Inga påhittade kundärenden, ingen uppdiktad anställning. Alla personer och ärenden är **simulerade**.

## Navigera i projektet
- [Steg-för-steg-installation](SETUP.md)
- [Sex praktiska supportärenden](TICKETS.md)
- [Ärendemall](TICKET_TEMPLATE.md)
- [Framsteg och bildbevis](PROGRESS.md)
- [CV, LinkedIn och intervju](FOR_EMPLOYERS.md)

## Officiell dokumentation
- [Microsoft — Active Directory Domain Services](https://learn.microsoft.com/sv-se/windows-server/identity/ad-ds/deploy/install-active-directory-domain-services--level-100-)
- [Microsoft — DHCP på Windows Server](https://learn.microsoft.com/sv-se/windows-server/networking/technologies/dhcp/quickstart-install-configure-dhcp-server)
- [Microsoft — Grupprinciper](https://learn.microsoft.com/sv-se/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console)
- [Microsoft — Windows 11 Enterprise Evaluation (90 dagar)](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-11-enterprise)
- [Microsoft — Windows Server 2025 Evaluation (180 dagar)](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2025)
- [Broadcom — VMware Virtual Network Editor](https://knowledge.broadcom.com/external/article/339371/using-the-virtual-network-editor-in-vmwa.html)

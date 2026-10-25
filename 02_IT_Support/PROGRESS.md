# Progress — verifierad status

**Senast uppdaterad:** 2026-10-25  
Detta dokument är en **ärlig statuslogg**. Att en instruktion finns i GitHub betyder inte att övningen är genomförd.

| Del | Status | Underlag |
|---|---|---|
| Windows Server 2025 VM | Dokumenterad som gjord | Se befintlig Lab 01 README |
| Statisk IP 10.0.0.1 | Dokumenterad som gjord | Se befintlig Lab 01 README och bilder |
| AD DS / domän lab.local | Dokumenterad som gjord | Se befintlig Lab 01 README och bilder |
| Separat isolerat VMware-nät | Inte verifierat | Lägg till datum och bild |
| Windows 11-klient | Inte verifierat | Lägg till datum och bild |
| DNS-funktion från klient | Inte verifierat | Lägg till datum och bild |
| DHCP-omfång och lease | Inte verifierat | Lägg till datum och bild |
| Domänanslutning LAB-PC01 | Inte verifierat | Lägg till datum och bild |
| Testanvändare / AD-grupper | Inte verifierat | Lägg till datum och bild |
| NTFS- och delningsbehörigheter | Inte verifierat | Lägg till datum och bild |
| GPO på testanvändare | Inte verifierat | Lägg till datum och bild |
| LAB-001 inloggning | Inte genomfört | Skapa ärendedokument |
| LAB-002 DHCP | Inte genomfört | Skapa ärendedokument |
| LAB-003 delad mapp | Inte genomfört | Skapa ärendedokument |
| LAB-004 GPO | Inte genomfört | Skapa ärendedokument |
| LAB-005 DNS | Inte genomfört | Skapa ärendedokument |
| LAB-006 onboarding | Inte genomfört | Skapa ärendedokument |

## Uppdateringsregel
- Ändra endast status till **Klart** efter att du testat och verifierat momentet.
- Lägg till datum, anteckning och en anonymiserad skärmbild i en separat ärendefil.
- Skriv vad som inte fungerade. Det visar felsökningsförmåga.
- Spara bilder i en underkatalog, t.ex. `evidence/LAB-001/`, när de finns på riktigt.
- Om ett labblösenord någonsin syns i materialet: byt det. Lösenord hör inte hemma i GitHub.

## Checklista för första passet
- [ ] Verifiera befintlig server-VM och AD-domän.
- [ ] Kontrollera att testnätet inte når hemmets LAN via bridged.
- [ ] Ta återställningspunkt.
- [ ] Skapa och starta klient-VM.
- [ ] Kontrollera Windows-klientens DNS till servern.
- [ ] Dokumentera en skärmbild och ett felsökningsfynd.

# Intervjubank — verkliga erfarenheter från IT-labb

Målet är att kunna förklara **redan genomförda moment** för junior IT-support. Inga påhittade kunduppdrag. Kontrollera datum, symptom, miljö och åtgärder mot egna anteckningar.

## Exempel 1 — Active Directory: förutsättningskontroll vid domänkontrollant
**Bevis:** Lab 01 README och tillhörande skärmbilder.

**Situationen:** Jag installerade Windows Server 2025 i VMware och byggde domänen `lab.local`. Vid förutsättningskontrollen inför DC-konfiguration uppstod ett fel.

**Vad jag gjorde:** Jag läste felmeddelandet, identifierade att administratörskontot saknade lösenord, rättade förutsättningen och slutförde installationen.

**Resultat:** Active Directory Users and Computers visade den skapade domänen.

**Vad det visar:** Metodisk felsökning, förmåga att läsa felmeddelanden och dokumentera arbetet.

**Kort intervjusvar:**
> I mitt eget labb installerade jag Windows Server 2025 och konfigurerade Active Directory. Under förutsättningskontrollen inför domänkontrollanten uppstod ett fel eftersom administratörskontot saknade lösenord. Jag följde felmeddelandet, korrigerade inställningen och kunde slutföra installationen. Efteråt kontrollerade jag domänen i Active Directory och dokumenterade processen på GitHub.

## Exempel 2 — DNS (tidigare AD-/certifikatövning, enligt egen uppgift)
**Vad du uppgett:** Du har arbetat med DNS och klienttestning i samband med tidigare Active Directory-studier.

Fyll i **innan** du använder det som en specifik löst incident:
- Vilken klient/server använde du?
- Vad var felet? [skriv verkligt fel, inte påhittat]
- Hur undersökte du om klienten använde rätt DNS-server?
- Vad visade dina tester?
- Vad ändrade du och vad fungerade efteråt?
- Vilket kursmaterial eller vilken skärmbild kan styrka det?

**Tekniskt resonemang vid hypotetisk fråga:** Kontrollera klientens IP/DNS, om klienten når servern, om domänuppslagning fungerar och om DNS-tjänsten har rätt poster. Ändra först när problemet är identifierat. Detta är en *felsökningsmetod*, inte ett påstående om vad som hände i din tidigare övning.

## Exempel 3 — DHCP / Windows 11-klient (tidigare AD-/certifikatövning, enligt egen uppgift)
**Vad du uppgett:** Du har installerat Windows 11 i VMware, arbetat med DHCP och gjort klienttester.

Fyll i:
- Hur var VMware-nätverket konfigurerat?
- Delade DHCP ut rätt IP och DNS-adress?
- Vilken kontroll genomförde du från Windows-klienten?
- Uppstod ett verkligt fel? Vad gjorde du då?
- Hur verifierade du det slutliga resultatet?

**Tekniskt resonemang vid hypotetisk fråga:** Verifiera klientens nätverksanslutning och IPv4-konfiguration, om adress tilldelas, DHCP-serverns scope/lease, konkurrerande DHCP och rätt DNS-inställningar. Detta är en övningsmodell, inte en återberättad incident.

## 60 sekunder — presentera dig
> Jag har utbildningsbakgrund inom dator- och nätverksteknik och har arbetat praktiskt med Windows Server, Active Directory och VMware i egna labb och övningar. Jag har bland annat satt upp en domänkontrollant och felsökt ett installationsproblem som jag dokumenterat på GitHub. Jag har också tidigare installerat Windows 11 i en virtuell miljö och övat DNS, DHCP och klienttestning. Nu söker jag en junior roll inom IT-support där jag får använda de kunskaperna för att hjälpa användare, felsöka systematiskt och utvecklas.

Anpassa formuleringen till en faktisk intervju och använd endast detaljer som du själv kan förklara.

## Felsökningsmodell att berätta högt
1. Lyssna och bedöm påverkan: en användare eller flera?
2. Ställ relevanta frågor och avgränsa felet.
3. Kontrollera enklaste sannolika orsakerna, en i taget.
4. Gör en ändring med rätt behörighet/godkännande.
5. Verifiera med användaren och dokumentera.
6. Eskalera om felet inte kan lösas inom ditt ansvar.

För inloggningsproblem: fastställ felmeddelande, om kontot fungerar någon annanstans, nätverks-/domänanslutning och AD-kontots status. Återställ inte ett lösenord utan korrekt identitetskontroll.

# Sex simulerade IT-supportärenden

> **Samtliga nedan är övningsscenarier, inte färdiglösta incidenter.** Börja med ett scenario i taget. Skapa ett separat ärendedokument per genomfört test från [mallen](TICKET_TEMPLATE.md).

| ID | Anmälan | Prioritet (övning) | Kunskap |
|---|---|---|---|
| LAB-001 | Kan inte logga in | P2 | Active Directory, konto, identitetskontroll |
| LAB-002 | Datorn får ingen IP-adress | P2 | DHCP, VMware-nätverk |
| LAB-003 | Kan inte öppna delad mapp | P3 | Grupper, NTFS, delningsbehörighet |
| LAB-004 | Gruppolicy gäller inte | P3 | OU, GPO, klientkontroll |
| LAB-005 | Domännamnet kan inte hittas | P2 | DNS och domänanslutning |
| LAB-006 | Ny medarbetare behöver konto | P3 | Onboarding, minsta behörighet |

**Prioriteringen är ett exempel.** I riktig first line sätts prioritet utifrån påverkan, antal berörda, brådska och verksamhetens regler — inte bara symptom.

## LAB-001 — "Jag kan inte logga in"
**Fiktiv användare:** Emma, Support.

- Förutsättning: labbkontot finns och klienten är domänansluten.
- Skapa säkert testsymptom: lås kontot med de vanliga administrativa labbinställningarna eller använd ett avsiktligt felaktigt testlösenord.
- Kontrollera: användarnamn/domän, kontostatus, låsning och om problemet gäller en eller flera datorer.
- Åtgärda endast efter **simulerad identitetsverifiering** i ärendet. Lås upp kontot eller återställ testlösenordet vid behov.
- Verifiera: användaren kan logga in. Dokumentera utan att skriva ut lösenord.

## LAB-002 — "Datorn saknar nätverk"
**Fiktiv användare:** Noah, Ekonomi.

- Förutsättning: DHCP-rollen är konfigurerad i det isolerade nätet.
- Skapa testsymptom: välj en avsiktligt felaktig klientkonfiguration, inte genom att utsätta hemmets nätverk.
- Kontrollera: nätverkskortets virtuella nät, IPv4-inställningar, DHCP-omfång och om en adress har delats ut.
- Åtgärda: återställ automatisk adresstilldelning eller korrigera inställningen i den isolerade testmiljön.
- Verifiera: klienten får en adress inom `10.0.0.100–10.0.0.150` och når servern.

## LAB-003 — "Åtkomst nekad till Support-mappen"
**Fiktiv användare:** Emma, Support.

- Skapa testsymptom: Emma finns inte i `SG-Support-RW`.
- Kontrollera: rätt resurs, relevant gruppmedlemskap och både delnings- och NTFS-rättigheter.
- Åtgärda: lägg till i gruppen **bara efter simulerat godkännande**, uppdatera inloggning vid behov.
- Verifiera: Emma kan skapa en testfil. Ett obehörigt testkonto kan inte göra samma sak.
- Dokumentera: varför gruppbaserade behörigheter är bättre än individuella undantag.

## LAB-004 — "Företagets inställning kommer inte fram"
**Fiktiv användare:** Sara, HR.

- Skapa testsymptom: testanvändaren placeras utanför den OU där labb-GPO:t gäller.
- Kontrollera: OU, GPO-länk, säkerhetsfiltrering och resultatet i Group Policy Results.
- Åtgärda: rätta OU-/GPO-scope i labbet.
- Verifiera: den avsedda inställningen börjar gälla på klienten.
- Dokumentera: varför policyer riktas mot rätt OU.

## LAB-005 — "Windows hittar inte domänen"
**Fiktiv användare:** ny klient i labbet.

- Skapa testsymptom: ange tillfälligt en felaktig DNS-adress i klientens isolerade konfiguration.
- Kontrollera: klientens DNS-adress, serverns DNS-tjänst, domänzon och anslutning på det privata VMware-nätet.
- Åtgärda: sätt klient-DNS till `10.0.0.1` och kontrollera domänuppslagning.
- Verifiera: Windows kan hitta `lab.local` och klienten kan domänanslutas.
- Dokumentera: varför externa DNS-servrar inte ska ersätta AD-DNS på en domänklient.

## LAB-006 — "Ny kollega börjar idag"
**Fiktiv användare:** nyanställd i Support.

- Kontrollera begäran och registrera simulerat godkännande från ansvarig.
- Skapa testkonto på rätt OU med unikt testlösenord och byte vid första inloggning om det passar ditt scenario.
- Tilldela endast godkända gruppbehörigheter.
- Verifiera: korrekt inloggning och exakt avsedd åtkomst till mappar.
- Avsluta ärendet med återkoppling och notera vem som skulle godkänna ändringen i en riktig organisation.

## För varje ärende: miniminivå för bevis
- En bild på **orsaken** (gärna före åtgärd).
- En bild på **ändringen** utan lösenord eller känsliga uppgifter.
- Ett tydligt **test efter åtgärd**.
- Kort beskrivning av **varför problemet uppstod**.
- Resultat märkt `Löst i labb` **endast om du faktiskt har testat lösningen**.

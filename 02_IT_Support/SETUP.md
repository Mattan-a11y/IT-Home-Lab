# Installationsguide — Lab 02

**Arbetsmetod:** Utför ett moment, kontrollera resultatet och dokumentera med en skärmbild innan du går vidare. Använd bara testanvändare och testsystem.

## 0. Kontrollera befintliga Lab 01
1. Starta din befintliga Windows Server 2025-VM i VMware.
2. Kontrollera att den befintliga domänen `lab.local` öppnas i **Active Directory Users and Computers**.
3. Kontrollera serverns aktuella IP och nätmask. Guidens exempel utgår från `10.0.0.1/24`.
4. Kontrollera att DNS-rollen finns och innehåller domänzonen.
5. Ta en VMware-snapshot innan ändringar. Snapshot är en teståterställning, inte en ersättning för riktig säkerhetskopiering.

## 1. Skapa ett privat VMware-nät
1. Öppna **Edit → Virtual Network Editor** i VMware Workstation.
2. Lägg till en ledig anpassad VMnet (t.ex. VMnet2) och konfigurera den för privat/host-only trafik.
3. Ställ in delnätet `10.0.0.0`, nätmask `255.255.255.0` om detta är förenligt med ditt befintliga labb.
4. Stäng av alternativet som låter **VMware:s DHCP-tjänst** dela ut adresser på detta nät.
5. Se till att ingen värdadapter eller annan virtuell enhet har samma IP som servern (`10.0.0.1`). Om nödvändigt: använd en isolerad VMnet utan värdadapter eller ge värdadaptern en ledig IP.
6. Koppla server-VM till denna VMnet. **Använd inte Bridged** medan du kör egen DHCP.
7. Verifiera att din VM och domän fortfarande fungerar efter bytet. Om inte: återställ tidigare VMnet och felsök nätinställningarna innan nästa steg.

För uppdateringar kan en separat NAT-adapter användas tillfälligt. Stäng av den när du testar DHCP och domän-DNS, annars kan resultatet bli missvisande. Microsofts utvärderingsversion av servern behöver också aktiveras via internet inom den tidsfrist Microsoft anger.

## 2. Installera en Windows-klient
1. Hämta en laglig installationsbild för Windows 11 **Enterprise Evaluation** från Microsofts Evaluation Center.
2. Skapa en ny VM i VMware med exempelvis 2 virtuella CPU, 4 GB RAM, 64 GB virtuell disk och kompatibla Windows 11-inställningar (inklusive TPM 2.0).
3. Ge VM:n namnet `LAB-PC01`.
4. Koppla den till **samma isolerade VMnet** som servern.
5. Installera Windows enligt installationsguiden. Evaluation är tidsbegränsad (90 dagar); skapa inga antaganden om permanent licens.

## 3. Verifiera kommunikation och DNS
1. Ge tillfälligt klienten en ledig statisk IPv4-adress, t.ex. `10.0.0.50`, nätmask `255.255.255.0`.
2. Ange DNS-servern `10.0.0.1`. Lämna gateway tom i ett isolerat nät utan router.
3. Kontrollera i Windows nätverksinställningar att klienten når serverns IP.
4. Kontrollera att klienten hittar domännamnet `lab.local`. Domänanslutning kräver fungerande domän-DNS.
5. Fungerar inte detta: kontrollera VMnet, subnet, Windows-brandväggens regler för relevanta tjänster och att DNS-tjänsten är igång. Öppna inte brandväggen brett som standardåtgärd.

## 4. Anslut klienten till domänen
1. Kontrollera att Windows-utgåvan stöder lokal Active Directory-domänanslutning (Pro/Enterprise/Education; inte Home).
2. Öppna **Inställningar → System → Om → Domän eller arbetsgrupp** (eller motsvarande avancerade systeminställningar).
3. Välj att ansluta datorn till domänen `lab.local` och ange en behörig labbadministratör.
4. Starta om och testa inloggning med ett domänkonto när kontot är skapat.

## 5. Bygg ett fiktivt företag i Active Directory
1. På servern, öppna **Active Directory Users and Computers**.
2. Skapa organisationsenheter (OU): `LAB-Users`, `LAB-Computers`, `LAB-Groups`.
3. Skapa tre fiktiva testkonton, t.ex. `emma.berg` (Support), `noah.lind` (Ekonomi), `sara.nilsson` (HR). Använd **unika testlösenord** som aldrig förekommer i dokumentationen.
4. Skapa säkerhetsgrupperna `SG-Support-RW` och `SG-HR-Read`.
5. Flytta `LAB-PC01` till `LAB-Computers`. Placera testanvändarna i avsedd OU.
6. Testa att låsa och låsa upp ett labbkonto enligt testscenarierna.

## 6. Sätt upp och testa DHCP
1. Kontrollera att nätet verkligen är isolerat och att **VMwares inbyggda DHCP är avstängt**.
2. I **Server Manager → Add Roles and Features**, lägg till DHCP Server om den saknas.
3. Öppna DHCP-konsolen och auktorisera servern i domänen.
4. Skapa ett IPv4-omfång: `10.0.0.100–10.0.0.150`, nätmask `255.255.255.0`.
5. Sätt DNS-server till `10.0.0.1` och domänsuffix till `lab.local`.
6. Ange **inte** en påhittad gateway. En gateway ska bara sättas om en riktig router finns på labbnätet.
7. Aktivera omfånget, byt sedan klientens nätverksinställningar till automatisk IPv4 och DNS.
8. Kontrollera att Windows-klienten får en adress inom omfånget och att den kan logga in i domänen.

## 7. Delade mappar och åtkomst
1. Skapa en testmapp på servern, t.ex. `D:\LabShares\Support` (eller valfri datavolym).
2. Dela den som `Support` och tilldela endast avsedda säkerhetsgrupper rättigheter.
3. Kontrollera **både delningsbehörigheter och NTFS-behörigheter**. Exempel: Support-gruppen får ändra, andra testanvändare nekas.
4. Testa med två olika testkonton. Spara både lyckat och nekad åtkomst som dokumentation.
5. Ge inte `Everyone` obegränsad åtkomst bara för att snabbt få scenariot att fungera.

## 8. En enkel GPO
1. Öppna **Group Policy Management**.
2. Skapa ett nytt test-GPO, t.ex. `LAB-User-Screen-Lock`, och länka det till din testanvändar-OU.
3. Konfigurera en lämplig användarinställning, t.ex. lösenordsskyddad skärmsläckare med timeout.
4. Logga in på klienten med en testanvändare och kontrollera att policyn slår igenom.
5. Vid fel: kontrollera OU, GPO-länk, säkerhetsfiltrering och **Group Policy Results** i administrationskonsolen.
6. Ändra inte breda domänstandardpolicyer för en enda labbövning.

## 9. Gör labbet till support-erfarenhet
- Kör de sex scenarierna i [TICKETS.md](TICKETS.md).
- Registrera varje test som ett simulerat ärende med [TICKET_TEMPLATE.md](TICKET_TEMPLATE.md).
- Fyll i [PROGRESS.md](PROGRESS.md) med exakt datum, resultat och länkar till egna bevis.
- Dokumentera en verklig misslyckad felsökning lika noggrant som en lyckad.

## Säkerhet och etik
Allt sker i virtuella, isolerade labbsystem. Publicera aldrig riktiga lösenord, tokens, privata IP-konfigurationer från någon arbetsgivare, känslig information eller verkliga personuppgifter. Sanera skärmbilder. Om en tidigare skärmbild visat ett labblösenord: byt lösenordet innan labbet återanvänds.

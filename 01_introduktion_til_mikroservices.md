# Introduktion til mikroservices
### Monolitiske applikationer
Når du laver en ny applikation vil den ofte starte ud med en monolitisk arkitektur.  
Kernen i en monolitisk struktur er forretningslogiken, der bliver implementeret af moduler, der definerer services, domaine objekter og events.  
Derudover har den interfaces, der kommuniker med en database, eksterne services som f.eks. at sende smser og et web UI.  
Et andet kendetegn er at en monolistisk applikation deployes med en fil f.eks. en java applikation deploys med en war fil og en node applikation er en packages med et directory hiraki.  
Monolitiske applikationer er meget almindelige.  
Fordelen ved monolistiske applikationer:  
1. De er enkle at udvikle.  
2. De er enkle at teste.  
3. De er lettet at deploye.  
4. Det er muligt at skaler ved at have flere applikationer bag en load balancer.  

### Udfordringer ved monolitiske applikationer
Med tiden har succesfulde applikationer en tendens til at vokse sig store. Der bliver tilføjet nye user stories, 
og en applikation kan ende med at består af flere millioner linjer kode.  
Ulemper:  
1. Det medfører at applikationen bliver meget kompleks. Det er ikke muligt for den enkelte udvikler at forstå hele applikationen. 
2. Det bestyder at det bliver svært og tager længere tid, når der skal fixes bugs og laves nye features. 
3. Det er en nedadgående spiral, da de nye features ikke vil blive implementeret korrekt, og dermed gøre koden endnu mere kompleks. 
4. Det kan medfører at der må bruges mere tid på manuelt at test, da man ikke med sikkerhed kan forudsige, hvordan andre features vil reagerer på en ny feature. 
5. Har du en error så vil hele applikation gå ned.
6. Derudover er det også sværer at implementer nye og bedre frameworks, da mere eller mindre hele applikationen skal omskrives til det nye framework. 
7. Det gør det sværere at implemter nyere og bedre teknologier.  





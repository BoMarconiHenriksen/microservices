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

### Mikroservices - Håndter kompleksiteten
Virksomheder som Amazon, Ebay og Netflix har løst dette problem ved at udvikle en backend, der består af en mikroservice arkitektur.  
I stedet for at bygge en stor monolitisk applikation, er ideen at splitte applikationen i mindre selvstændige services, der er forbundet.  

En service implementer typiske en feature eller funktionalitet. Det kan f.eks. være ordrebehandling, kundehåndtering etc. Hver service har sin egen arkitektur bestående af foretningslogik. Nogen mikroservices har en API, der kan blive brugt af andre mikroservices eller af applikationsens klienter. Andre mikroservices implementer måske web UI. Ved runtime er hver instans af applikationen en cloud vm eller docker container(er hurtigere).  

Eksemple på opdeling af et system i mikroservices.  
![alt text](https://github.com/BoMarconiHenriksen/microservices/blob/master/img/Richardson-microservices-part1-2_microservices-architecture.png)  

Hvert område af applikationen har nu sin egen mikroservice. Derudover er webapplikationen delt op i flere simplere web applikationer. Dette gør det lettere at deploye specifikke web UI til forskellige brugere og devices.  

##### Inter-service communication
Hver backend har et REST API, og de fleste services bruger de andre services APIer. De to UI services bruger f.eks. andre services for at kunne render web sider. Services kan også bruge asynkrone besked baseret kommunikation. Det hedder inter-service communication, og det kan du læse mere om her LINK!!!   

##### API Gateway
I eksemplet har mobil applikationen ikke direkte adgang til backend services. I stedet går kommunikationen igennem en API gateway https://microservices.io/patterns/apigateway.html  
En gateway er ansvarlig for load balancing, caching, adgangskontrol, API metering, and monitorering.  

##### The Scale Cube
Bogen The Art of Scaling http://theartofscalability.com/ beskriver en skaleringsmodel, der hedder the scale cube. Den beskriver 3 dimention i skalering.  

Y skaler ved at opdele. X skaler ved at køre flere kopier af samme instance bag en load balancer, og z skalering, hvor f.eks. primary key til en kunde bruges til at lede requestet hen til en bestemt server. https://microservices.io/articles/scalecube.html   
![alt text](https://github.com/BoMarconiHenriksen/microservices/blob/master/img/DecomposingApplications.021.jpg)  

Typisk bruges de 3 skaleringsmetoder sammen. Y skalering opdeler applikationen i mikroservices. Ved runtime kører x skalering flere instanser af hver service bag en load balancer. Nogen applikationer bruger også z skalering til at partition the service. En trip management service med docker containere kunne se sådan ud.  
![alt text](https://github.com/BoMarconiHenriksen/microservices/blob/master/img/Richardson-microservices-part1-4_dockerized-application.png)  

##### Databaser
En mikroservice arkitektur påvirker relationen mellem en applikation og en database. I stedet for at dele et database schema har hver mikroservice sin egen database schema. Det kan resultere i at data nogen data kan blive dublikeret. På den anden side er det essientielt at have en database per mikroservice, da det sikrer en lav kopling.  
![alt text](https://github.com/BoMarconiHenriksen/microservices/blob/master/img/intro-microservices.png)  

Hver service har sin egen database. Derudover er det muligt at bruge den database, der er best egnet til den specifikke mikroservice.  

### Fordelene ved microservices





Det var stort fokus på distribuerte systemer og streams på Strangeloop i år.
Jon Moore startet fredagen med å presentere sin forskning på hvordan man kan oppnå 
både kausalitet mellom hendelser og synkroniserte klokker i distribuerte systemer.
Løsning hans bygger på teorien om hybride lamport clocks, og heter 'Distributed 
Monotonic Clocks', hvor han bruker flokkteori (insert eksempel på flokk-algoritme her som eksempel)
for å synkronisere klokker i en cluster av maskiner uten at alle maskinene
må kommunisere.

Peter Bailis(insert pun om game of thrones) forteller oss hvordan det å 
designe systemer mot worste case scenario istedet for average case scenario
i noen tilfeller kan gi bedre ytelse i avarge case scenario. 
'Alle' systemer er distribuert. Og som vi alle vet, så vil nettverket alltid feile. 

Ett godt eksempel er micro services. Si at avg. response time på requester er 1.2 ms,
og 99.th percentile response time er 100ms.
Hvis man øker ytelsen med 10% så vil avg latency gå fra 1.2 ms -> 1.09 ms,
mens 99.9th %ile går fra 100ms -> 10ms. Det er en veldig liten gevinst når man har 
en server, for man vil veldig skjeldent havne i worst-case scenario uansett.

MEN dersom du har 100 servere (her må jeg se på vidoen for å hente matten!)
vil man med forrige optimalisering få avg. latency 64ms -> 6.7ms.

quote: Your service's corner case may be its consumer's average case.

Design for worst case scenario når:
* Corner cases are common
* Environmental conditions are variable
* When "normal" isn't as normal as you think

Defining "normal" defines our designs. 

Det er jo ofte stort fokus på å bygge stateless services som er lett å skalere. 
Men er servicene våre virkelig stateless? Catie McCaffrey forteller at oss stateless 
services flytter state ned til databasen. Men i noen tilfeller så kan det lønne
seg å designe services som tar vare på state.
For eksempel så bruker Uber sticky sessions under kjøreturen, og de har designet
systemet slik at klienten alltid havner hos samme server, som har cachet all state
for å øke ytelsen. Så neste gang vi designer en service så kan vi jo tenke på om 
vi det kan lønne seg å bygge state inn i servicen?

Mannen bak Kafka, Jay Kreps, gir en introduksjon til stream processing som ett 
tredje prosseseringsparadigme i tillegg til de klassiske paradigmene request/response 
og batch processing.
Hvis du er ny til stream processing så anbefaler vi å ta en titt på foredraget.
Og hvis du ønsker å lære mer om streams i frontend-koden din så gir Pam Selle en
introduksjon til hva streams er og hvordan man kan jobbe med streams i javascript.



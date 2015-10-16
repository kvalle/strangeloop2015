Det var stort fokus på distribuerte systemer og streams på Strangeloop i år.

Jon Moore startet fredagen med å presentere sin forskning på hvordan man kan oppnå 
både kausalitet mellom hendelser og synkroniserte klokker i distribuerte systemer.
Løsning hans bygger på teorien om hybride lamport clocks, og heter 'Distributed 
Monotonic Clocks', hvor han bruker flokkteori (insert eksempel på flokk-algoritme her som eksempel)
for å synkronisere klokker i en cluster av maskiner uten at alle maskinene
må kommunisere.

> Video: [How to Have your Causality and Wall Clocks, Too - by Jon Moore](https://youtu.be/YqNGbvFHoKM)

Peter Bailis(insert pun om game of thrones) forteller oss hvordan det å 
designe systemer for worste case scenario istedet for average case scenario
i noen tilfeller kan gi bedre ytelse i avarge case scenario. 

Your service's corner case may be its consumer's average case.

Design for worst case scenario når:
* Corner cases are common
* Environmental conditions are variable
* When "normal" isn't as normal as you think

Defining "normal" defines our designs. 

> Video: ["When "Worst" is Best (in Distributed Systems)" by Peter Bailis](https://youtu.be/ZGIAypUUwoQ)

Det er jo ofte stort fokus på å bygge stateless services som er lett å skalere. 
Men er servicene våre virkelig stateless? Catie McCaffrey forteller at oss stateless 
services ofte flytter state ned til databasen. Men i noen tilfeller så kan det lønne
seg å designe services som tar vare på state i applikasjonen, noe de for eksempel har gjort i tjenesten Uber.

> Video ["Building Scalable Stateful Services" by Caitie McCaffrey](https://youtu.be/H0i_bXKwujQ)

Mannen bak Kafka, Jay Kreps, gir en introduksjon til stream processing som ett 
tredje prosseseringsparadigme i tillegg til de klassiske paradigmene request/response 
og batch processing.

> Video ["Apache Kafka and the Next 700 Stream Processing Systems" by Jay Kreps](https://youtu.be/9RMOc0SwRro)

Hvis du er ny til stream processing så anbefaler vi å ta en titt på foredraget.
Og hvis du ønsker å lære mer om streams i frontend-koden din så gir Pam Selle en
introduksjon til hva streams er og hvordan man kan jobbe med streams i javascript.

> Video ["Streams: The data structure we need" by Pam Selle](https://youtu.be/3iKkwzlch0o)  

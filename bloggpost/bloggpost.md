![Got Loop?](https://bekkopen.blob.core.windows.net/attachments/1976802f-7a9c-4c57-b6c5-8c131e40df4a)

# Strange Loop 2015

**Strange Loop er en spennende konferanse for softwareutviklere som arrangeres årlig i St. Louis, Missouri. Konferansen har et bredt spekter av tema, slik som programmeringsspråk, alternative databaser, concurrency, distribuerte systemer og sikkerhet, og fokuserer mer på teknologi enn på prosess.**

**Årets konferanse – den syvende i rekka – ble nylig arrangert, og BEKK var til stede.**

Det var i år mye fokus på problemstillinger relatert til distribuerte systemer. Kanskje ikke så overaskende, slik som mikrotjenester er i vinden om dagen. Vi kommer tilbake til dette, men vil først nevne et par andre foredrag vi synes var svært gode.

## Teknologi i aktivisme og undertrykkelse

Et av foredragene som sitter sterkest igjen hos oss etter konferansen var keynoten Idalin "Abby" Bobé holdt. Kanskje fordi denne touchet litt mer alvorligere tema enn en vanligvis får servert på en teknologikonferanse. 

Hun fortalte om sin bakgrunn, om oppveksten med minoritetsbakgrunn i fattige strøk i Philadelphia, og om det arbeidet hun gjør i dag. Bobé er, i tillegg til å være konsulent i ThoughtWorks, en selvutnevnt tech-aktivist. Hun fokuserer på hvordan teknologi kan brukes til å hjelpe folk som trenger det, både direkte og ved å skape oppmerksomhet rundt viktige saker.

![Idalin "Abby" Bobé talks about tech activism](https://bekkopen.blob.core.windows.net/attachments/c7d43538-81a0-4978-95a9-e0574dc53b6e)

[*Foto: Michael Bridge*](https://www.flickr.com/photos/strangeloop2015/21955796756/in/photostream/)

Både Bobé og andre i ThoughtWorks har vært i Ferguson i forbindelse med urolighetene der, og hun malte et tydelig bilde av hvordan teknologi har bidratt – både på godt og ondt. Selv om teknologi har spilt en viktig rolle for aktivistene for å få delt det som skjer med resten av verden, og for å få fokus på ting myndighetene forsøker å skjule, så har også teknologien blitt brukt imot dem.

Som teknologer har vi mange muligheter, og det er viktig å tenke igjennom hvordan vi bruker dem.

> Video: ["From Protesting to Programming: Becoming a Tech Activist" by Idalin "Abby" Bobé](https://youtu.be/gy82S8tjJX8)  

En annen keynote, av Morgan Marquis-Boire, fortsatte på sett og vis denne tråden. Mannen har lang fartstid innen sikkerhetsfeltet, og har sett mange trussler på nært hold.

Han fortalte om mange av dem som velger å bruke teknologi til ondt, og om insentivene som driver dem. Vi fikk høre om alt fra dedikerte cyberangrepsteam til hacking-verktøy solgt som hyllevare, hvem som bruker slikt, og hva det typisk brukes til.

Vi fikk servert en rekke anekdoter fra ting han har opplevd i arbeidet sitt, ispedd en god dose humor underveis, men også med mange alvorlige poeng.

Foredraget er overhodet ikke teknisk, men er en god tankevekker og en påminnelse om en del ting det er lett å glemme om en ikke jobber med sikkerhet til daglig.

> Video: ["Security for Humans: Privacy and Coercion Resistant Design" by Morgan Marquis-Boire](https://youtu.be/k4ypqzOShZs)


## λ calculus, et universelt programmeringspråk

Et annet foredrag vi absolutt vil anbefale å se, i alle fall om du er interessert i programmeringspråk eller logikk, er Philip Wadler sin presentasjon. Mannen er ikke bare en legende i programmeringspråkmiljøet, men også en karismatisk og morsom foredragsholder.

![Philip Wadler - Enter the Monad](https://bekkopen.blob.core.windows.net/attachments/7d214716-e348-48ab-86e4-531c47d74d15)

[*Foto: Michael Bridge*](https://www.flickr.com/photos/strangeloop2015/21794046360/)

Foredraget starter med en kort historiefortelling om programmeringens spede begynnelse. Vi ser hvordan [lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus), [rekursive funksjoner](https://en.wikipedia.org/wiki/Computable_function) og [turingmaskiner](https://en.wikipedia.org/wiki/Turing_machine) alle dukket opp samtidig. Er matematikk noe som blir oppdaget, eller er det noe som blir oppfunnet av matematikere? Wadler argumenterer for det førstnevnte, og at det samme dermed gjelder lambda calculus.

> "Most of you use programming languages that are invented. And you can tell, can't you? This is my invitation to you: to use programming languages that are discovered."

Han presenterer videre [Gentzens regler for deduksjon](https://no.wikipedia.org/wiki/Naturlig_deduksjon), og hvordan disse kan sees som et typesystem for lambda calculus. Preposisjoner er her ekvivalente med typer, bevis med programmer, og normalisering (forenkling) av bevis blir det samme som evaluering av programmer. Det er denne sammenhengen som er kjent som [Curry–Howard korrespondansen](https://en.wikipedia.org/wiki/Curry–Howard_correspondence).

> "Every good idea will be discovered twice. Once by a logician, and once by a computer scientist."

Det er mange morsomme poeng underveis, og vi er innom alt fra filmen Independence Day til multiverses. Et fremragende foredrag, såfremt du ikke er redd for noen slides med litt logikk.

<blockquote class="twitter-tweet" lang="en"><p lang="en" dir="ltr">so, this happened <a href="http://t.co/ju4wMSUily">pic.twitter.com/ju4wMSUily</a></p>&mdash; david crespo (@davidcrespo) <a href="https://twitter.com/davidcrespo/status/647865485162381312">September 26, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

> Video: ["Propositions as Types" by Philip Wadler](https://youtu.be/IOiZatlZtGU)


## Distribuerte systemer

Det temaet det helt klart var flest foredrag om på årets Strange Loop var distribuerte systemer. Her er det flere gode foredrag å velge mellom.

Jon Moore startet fredagen med å presentere sin forskning på hvordan man kan oppnå både kausalitet mellom hendelser, samt synkroniserte klokker i distribuerte systemer. Løsning hans bygger på teorien om hybride lamport clocks, og heter 'Distributed Monotonic Clocks', hvor flokkteori (som beskriver hvordan ett sett med individer koordinerer bevegelsene sine i en gruppe) brukes til å synkronisere klokker i en cluster av maskiner uten at alle maskinene må kommunisere med hverandre.

![Flock of geese](https://bekkopen.blob.core.windows.net/attachments/3dc6f416-9840-485a-8f5c-85b49586e5b2)

[*Foto: Tim Evanson*](https://www.flickr.com/photos/23165290@N00/13783370045/)

> Video: ["How to Have your Causality and Wall Clocks, Too" by Jon Moore](https://youtu.be/YqNGbvFHoKM)

Peter Bailis (insert pun om Game of Thrones her) forteller oss hvordan det å designe systemer for optimalisere worst case scenario istedet for average case scenario i noen tilfeller kan føre til bedre ytelse i average case scenario.

Men hvorfor skal man bry seg om systemets worst case scenario? Worst case scenarios er jo edge cases som skjeldent vil intreffe. Men systemets corner case kan være brukerens average case. Det å definere hva som er "normalt" i systemet definerer designet vårt. 

Design for worst case scenario når:

* Corner cases er vanlige 
* Miljøets tilstand er variabel 
* "Normalt" ikke er så normalt som man tror

> Video: ["When "Worst" is Best (in Distributed Systems)" by Peter Bailis](https://youtu.be/ZGIAypUUwoQ)

Det er ofte stort fokus på å bygge tilstandsløse tjenester som er lett å skalere. Men er tjenestene våre virkelig tilstandsløse? Catie McCaffrey forteller oss at tilstandsløse tjenester ofte flytter tilstanden ned til databasen. Men i noen tilfeller så kan det lønne seg å designe tjenester som tar vare på tilstanden i applikasjonen, noe de for eksempel har gjort i tjenesten Uber.

> Video: ["Building Scalable Stateful Services" by Caitie McCaffrey](https://youtu.be/H0i_bXKwujQ)

Mannen bak Kafka, Jay Kreps, gir en introduksjon til stream processing som ett tredje prosseseringsparadigme i tillegg til de klassiske paradigmene request/response og batch processing.
Hvis stream processing er et ukjent begrep for deg så anbefaler vi å ta en titt på foredraget. 

> Video: ["Apache Kafka and the Next 700 Stream Processing Systems" by Jay Kreps](https://youtu.be/9RMOc0SwRro)

Og hvis du ønsker å lære mer om streams i frontend-koden din så gir Pam Selle en introduksjon til hva streams er og hvordan man kan jobbe med streams i JavaScript.

> Video: ["Streams: The data structure we need" by Pam Selle](https://youtu.be/3iKkwzlch0o)  

Dette var bare en smakebit over det som ble servert på Strange Loop i år. Vi har listet våre favoritter, men vi rakk ikke å se alle foredragene. En komplett liste over foredragene er [tilgjengelig på YouTube](https://www.youtube.com/playlist?list=PLcGKfGEEONaCIl5eU53uPBnRJ9rbIH32R).

## TL;DR

Distribuerte systemer er vanskelig.

![Everything is fine](https://bekkopen.blob.core.windows.net/attachments/897149ed-8471-4ebc-a52a-227d259814f9)

Sonic Pi 
The live coding synth for everyone

Musikk-editor implementert i ruby

created for school children
used by a lot lot of different people

10-åringer i england har laget egne SonicPI-band, etter å ha lært seg selv hvordan det fungerer.

Normally talk about why and what,
This time, talk about technical internal aspects


play/sleep
in_thread
with_fx
live_loop
...


start med minst mulig oppsett:

	play 80

play: "have fun"
80: "how much fun you want"

numbers goes up and down, like pitch

> People talks about tests and types, right. I don't have any of those. What you do need is proofs!

problem: ting som sleep, og andre ting føre til "time drift".
har re-implementert rubys sleep

semantikken til "sleep" blir ikke lenger "sleep at least x seconds", men sov differansen som trengs for å synke diffen til ønsket tidspunkt. Tar vare på tidspunktet prosessen/musikken starter, og opererer med "virtual time".

Hvis virtuell tid kommer for langt bak:

	eks: spiller uendelig mange noter samtidig:

	loop do
		play 80
	done

	"TimingException: thread got too far behind time."

Vil spille ting samtidig: concurrency!

	in_thread do
		3.times do
			play 79
			sleep 1
		end
	end

	play 90

in_thread starter en egen tråd for spillingen. Bygget på toppen av ruby-tråder.

videre: hvordan få til effekter? piping er ikke særlig musikalsk...

- bruker Reverb, og piper lydene igjennom

problem: hvordan få unger til å skjønne at de må lukke Reverbs, og alt slikt? løser dette med ruby blocks

	with_fx :echo do
		play 80
	end

	oppretter :echo-reverb før blokka, og rydder opp etterpå, men først etter at alle lydene i blokka er ferdige å spille.

problem: kan fortsatt ikke endre koden live. kan bare komponere, og så spille av.

når "play" trykkes vil vi ikke at alle definerte tråder skal startes på nytt (i paralell)

tråder kan navngis. når en restart/^S re-evaluerer og starter koden, vil den aldri starte to tråder med samme navn. hvis en navngitt tråd allerede kjører, startes den ikke på nytt.

live_loop er en forenkling, som slår sammen funksjonsdefinisjon, looping og navngitte loops.

	live_loop :foo do
		with_fx :reverb do
			play 35
			sleep
		end
	end

mye enklere å bruke, slik at unger kan bruke tråder og livekode

- cue/sync

hvis en gjør en feil i livekodeingen, som fører til en exception, kan trådene komme ut av sync

cue og sync løser dette

"sync :foo" venter på en :foo fra en hvilken som helst annen tråd
"cue :foo" sender signalet til alle andre tråder, slik at alle sync-ventere kjører videre

live_loop gjør også en implisitt "cue" hver gang de starter. Anre live_loops kan derfor synkes opp ved å sync-e på navnet på loopen.

dette gjør at en kan fint gjøre feil under live-koding, hvor bare deler av systemet går ned, og en har muligheten til å fikse det igjen


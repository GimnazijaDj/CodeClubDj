---
title: Uhvati točke
level: Scratch 2
language: hr-HR
stylesheet: scratch
embeds: "*.png"
materials: ["Club Leader Resources/*", "Project Resources/*"]
beta: true
...

# Uvod { .intro }

U ovom projektu naučit ćeš kako kreirati igru u kojoj moraš uskladiti obojane točkice sa točnim dijelovima kontrolera.

<div class="scratch-preview">
  <iframe allowtransparency="true" width="485" height="402" src="http://scratch.mit.edu/projects/embed/44942820/?autostart=false" frameborder="0"></iframe>
  <img src="dots-final.png">
</div>

# Korak 1: Izrada kontrolera { .activity }

Počnimo s izradom kontrolera koji će se koristiti kako bi se prokupile točke. 

## Zadaci { .check }

+ Otvori novi Scratch projekt i obriši lik mačke da dobiješ prazan projekt. Možeš koristiti online Scratch editor koji se nalazi na adresi <a href="http://jumpto.cc/scratch-new">jumpto.cc/scratch-new</a>.

+ Ako imaš pristup do mape 'Resources' ili slike 'controller.svg' klikni ikonu 'Učitaj lik iz datoteke' i dodaj sliku 'controller.svg'. Premjesti ju u centar pozornice.

	![screenshot](dots-controller.png)
	
	Ako nemaš tu sliku, nacrtaj ju!
	
+ Okreni kontroler desno kada se pritisne desna strelica na tipkovnici:

	```blocks
		kada je ⚑ kliknut
		ponavljaj
   			ako <tipka [strelica desno v] pritisnuta?> onda
      				skreni ↻ (3) stupnjeva
   			end
		end
	```
+ Pokreni projekt i isprobaj kontroler - trebao bi se vrtiti u desno.

## Spremi projekt. { .save }

## Izazov: Okretanje u lijevo {.challenge}
Možeš li napraviti da se kontroler okreće u lijevu stranu kada se pritisne lijeva strelica na tipkovnici?

## Spremi promjene u projektu. { .save }

# Korak 2: Skupljanje točaka { .activity }

Dodajmo nekoliko točaka kako bi ih igrač pokupio s kontolerom.

## Zadatci { .check }

+ Kreiraj novog lika koji se zove 'red'. Taj lik bi trebao biti mala crvena točka.

	![screenshot](dots-red.png)

+ Točki dodaj sljedeće naredbe kako bi se svakih nekoliko sekundi kreirao njezin duplikat:

	```blocks
		kada je ⚑ kliknut
		čekaj (2) sekundi
		ponavljaj
   			kloniraj [ja v]
   			čekaj (slučajni broj od (5) do (10)) sekundi
		end

	```

+ Kada god se pojavi duplikat, želiš da se pojavi u jednome od četiri kuta pozornice.

	![screenshot](dots-start.png)

	Kako bi to napravili najprije kreiraj novu listu koja se zove `početak` {.blockdata}, klikni na znak `(+)`i dodaj vrijednosti `-180` i `180`.

	![screenshot](dots-list.png)

+ Ta dva elementa liste možeš koristiti za odabiranje nasumičnog kuta pozornice. Sljedeće naredbe dodaj liku 'točke' kako bi se svaki novi duplikat pojavio u nasumičnom kutu, a onda se polako kretao prema kontroleru.

	```blocks
		kada krećem kao klon
		idi na x:(element (random v) iz [početak v]) y:(element (random v) iz [početak v])
		okreni se k [controller v]
		prikaži
		ponavljaj dok nije <dodiruje [controller v]?>
   			idi (1) koraka
		end
	```

	Naredbama iznad odabiremo vrijednost `-180` ili `180` za x _i_ y pozicije točke, što znači da će svaki puta duplikat krenuti iz jednog kuta pozornice.

+ Testiraj projekt. Trebaš vidjeti puno crvenih točaka koje se pojavljuju u svakome uglu ekrana i polako se pokreću prema kontroleru.

	![screenshot](dots-red-test.png)

+ Napravi dvije nove varijable koje se zovu`lives` {.blockdata} i `score` {.blockdata}.

+ Dodaj kod na pozornici kako bi postavio `lives` {.blockdata} ma 3 i `score` {.blockdata} na 0 na početku igrice.

+ Trebaš dodati ovaj kod na kraj koda `when I start as a clone` {.blockcontrol} crvene točke, tako da se 1 bod dodaje igračevu `score` {.blockdata} ako se boje poklapaju, ili se 1 oduzima iz igračevih `lives` {.blockdata} ako se boje ne poklapaju.

	```blocks
		move (5) steps
		if <touching color [#FF0000]?> then
			change [score v] by (1)
			play sound [pop v]
		else
			change [lives v] by (-1)
			play sound [laser1 v]
		end
		delete this clone
	```

+ Dodaj ovaj kod na kraj pozornicine (script) tako da igra završi kada igrač izgubi sva 3 života:

	```blocks
		wait until <(lives) < [1]>
		stop [all v]
	```

+ Testiraj igricu da vidiš radi li kod kako treba.

## Spremi promjene u projektu { .save }

## Izazov: Više točaka {.challenge}
Dupliciraj svoga lika 'red' točku dva puta i imenuj dva nova lika 'yellow' i 'blue'.

![screenshot](dots-more-dots.png)

Uredi te likov (uključujući i njihov kod), tako da svaka točka odgovara boji kontrolera. Nemoj zaboraviti testirati svoj projekt i uvjeriti se da igrač dobije bodove i gubi živote kako bi i trebao, i da igra nije previše lagana ili previše teška.

![screenshot](dots-all-test.png)

## Spremi promjene u projektu { .save }

# Korak 3: Povećavanje težine { .activity .new-page}

Napravimo da igrica postaje sve teža što dulje ju igrač igra, polako smanjujući razmak između točaka koje se pojavljuju.

## Zadaci { .check }

+ Napravi novu varijablu koja se zove `delay` {.blockdata}.

+ Na pozornici, napravi novi (script) koji postavlja delay na visoki broj, a onda polako reducira vrijeme odgode (delaya).

	```blocks
		when flag clicked
		set [delay v] to (8)
		repeat until < (delay) = (2)>
			wait (10) secs
			change [delay v] by (-0.5)
		end
	```

	Primijeti da je ovo vrlo slično načinu na koji radi odbrojavanje igre!

+ Možeš korisiti `delay` {.blockdata} varijablu u svojim crvenim, plavim i žutim (scripts). Ukloni kod koji čeka nasumičan broj sekundi prije izrade duplikata i zamijeni ga s novom `delay` {.blockdata} varijablom: 

	```blocks
		wait (delay) secs
	```

+ Testiraj svoju novu `delay` {.blockdata} varijablu i vidi reducira li se razmak između točaka. Radi li to za sve 3 boje točaka? Možeš li vidjeti da se vrijednost `delay` {.blockdata} varijable reducira?

## Spremi promjene u projektu { .save }

## Izazov: Brže kretanje točaka {.challenge}
Možeš li poboljšati igru dodajući varijablu `speed` {.blockdata}, tako da se točke počnu kretati korak po korak, i polako postaju sve brže? To će raditi na vrlo sličan način kao `delay` {.blockdata} varijabla koju smo koristili gore. Taj kod ti može pomoći.

## Spremi promjene u projektu { .save }

# Korak 4: Najbolji rezultat { .activity }

Spremimo najbolji rezltat kako bi igrači vidjeli kako im ide.

## Zadaci { .check }

+ Napravi novu varijablu koja se zove `high score` {.blockdata}.

+ Klikni na pozornicu i napravi novi blok naredbi `check high score` {.blockmoreblocks}.

	![screenshot](dots-custom-1.png)

+ Dodaj novi blok naredbi taman prije završetka igre.

	![screenshot](dots-custom-2.png)

+ Dodaj ovaj kod svom bloku naredbi kako bi spremio trenutni `score` {.blockdata} kao `high score` {.blockdata} `if` {.blockcontrol} je to najbolji rezultat do sada:

	```blocks
		define [check high score]
		if <(score) > (high score)> then
			set [high score v] to (score)
		end
	```

+ Testiraj kod. Igraj igricu kako bi provjerio mijenja li se`high score` {.blockdata} kako bi trebao.

## Spremi promjene u projektu { .save }

## Izazov: Poboljšaj svoju igru! {.challenge}
Možeš li smisliti načine na koje ćeš poboljšati svoju igru? Na primjer, možeš napraviti posebne točke koje:

+ poduplaju tvoj rezultat;
+ usporavaju točke;
+ skrivaju sve druge točke na ekranu!

## Spremi promjene u projektu { .save }

## Izazov: Izbornik {.challenge}
Možeš li dodati izbornik (sa gumbima) u igricu? Trebaš dodati ekran sa instrukcijama, ili odvojeni ekran koji će pokazivati najbolji rezultat. Ako trebaš pomoć s time, projekt 'Mozgalica' će ti pomoći.

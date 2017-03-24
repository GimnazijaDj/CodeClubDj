---
title: Izlazak sunca — Bilješke za vođe kluba
language: hr-HR
embeds: "*.png"
materials: [""]
...

#Uvod:
U ovom projektu djeca će učiti kako animirati pomoću CSS-a. Oni će učiti CSS @keyframes pravilo kako bi animirali razna svojstva slika i div-ova.

#Online Resursi

Preporučavamo korištenje [trinket](https://trinket.io/) kako bi kodirali u HTML & CSS online. Ovaj projekt sadrži sljedeće trinkete:

+ ['Sunrise' starting point](https://trinket.io/html/web-sunrise)

Također postoji trinket koji sadrži jednostavna rješenja izazova:

+ ['Sunrise' Finished](https://trinket.io/html/abcc0284a3)

#Offline Resursi
Ovaj projekt može biti [izvršen offline](../offline.html) ako to želite. Također imate pristup projektnim resursima klikom na 'Download Project Materials' link za ovaj projekt. Ovaj link sadrži 'Project Resources' mapu koja sadržil resurse koji će trebati da riješe ovaj projekt offline. Uvjerite se da svako dijete ima pristup kopiji tih resursa. Ova mapa sadrži sljedeće datoteke:

+ template/index.html
+ template/prefix.js
+ template/style.css
+ sunrise/index.html
+ sunrise/style.css
+ sunrise/prefixfree.js
+ sunrise/boat.png
+ sunrise/cloud.png
+ sunrise/helicopter.png
+ sunrise/rainbow.png
+ sunrise/sun.png

Također možete naći konačnu verziju projektnih izazova u 'Volunteer Resources' mapi koja sadrži:

+ index.html
+ style.css
+ prefixfree.js
+ boat.png
+ sun.png
+ rainbow.png

#Cilj učenja
+ Uređivanje i animiranje u CSS-u:
	+ Upoznavanje @keyframes` pravila za definiranje koraka u animaciji.
	+ Povečavanje korištenja svojstava koji definiraju veličinu, oblik, poziciju i boju elemenata na web stranici.

#Izazovi
+ "Diagonal animation" - uređivanje animacijskih `@keyframe` svojstava da koriste (left:);
+ "Improve the sky" - dodavanje više keyframeova i postavljanje pozadine (background:).
+ "More animation" - animiranje više slika i elemenata korištenjem različitih CSS svojstava. 

#Redovito pitana pitanja

+ Ovaj projekt koristi javascript `prefixfree.js` knjižnicu kako bi imali podudaranost animacije između različitih preglednika. Ako ova knjižnica nije u uporabi onda će dijeca koja koriste starije preglednike morati prilagoditi animaciju za njihov preglednik, naprimjer:

```
animation: sky 10s infinite; 		  	// Za sve novije preglednike
-webkit-animation: sky 10s infinite;  	// Za Webkit preglednike(Chrome, Safari...)
-moz-animation: sky 10s infinite;     	// Za Mozilla preglednike
-o-animation: sky 10s infinite;       	// Za Opera preglednike
-ms-animation: sky 10s infinite;		// Za Microsoft preglednike 
```
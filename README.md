# Eksperimenter med lys og dataoptagelse

![microbit_closeup](/IMAGE/microbit_closeup.jpg)

Vi skal prøve at måle lysintensiteten som er i rummet omkring microbitten. Lys måles normalt i [LUX](https://da.wikipedia.org/wiki/Lux) som er [SI-enhed](https://da.wikipedia.org/wiki/Syst%C3%A8me_International_d%27Unit%C3%A9s) for måling af belysningsstyrke. I vores forsøg og eksperimenter med microbitten bliver vores målinger oversat (translateret) til en analog elektrisk spænding. Denne analoge spænding kan veksle mellem 0 og 3 Volt. (enheden Volt er opkaldt efter [Alessandro Volta](https://da.wikipedia.org/wiki/Alessandro_Volta). 0 Volt vil sige intet lys, og som i nok allerede har gættet 3 Volt vil sige MEGET lys. Microbitten omdanner den målte værdi til et heltal, et tal mellem 0 og 1023. I computersprog hedder det en Integer. [Hvorfor 1023??](#hvorfor-1023)

Måling af lysniveau og afstand mellem solopgang og solnedgang er blandt andet blevet brugt til [tracking af dyr](#tracking-af-dyr)

Vores målinger kan vi bruge til mange forskellig opgaver, foreksempel:
* En alarm som ringer når nogen tænder lyset på dit værelse
* Tænde udendørslys når det bliver for mørkt
* Tilpasse lysniveau i et rum efter narturligt lys som kommer ind i rummet
* Lave et diagram over solen som står op

Vi skal arbejde med programmering både i [Microsoft MakeCode](https://pxt.microbit.org/)

![blocks](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/blocks_light_level01.png)

og [MicroPython](http://python.microbit.org/editor.html)



Vi kan måle lysniveauet på forskellige måder, så lad os bare komme i gang vi starter ud med en simpel måde:

# [Eksperiment nr. 1](/docs/first_experiment.md)
# [Eksperiment nr. 2](/docs/sec_experiment.md)


![måling af lys](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/measuring_light_alm2.jpg)


# Hvorfor 1023

I microbitten sidder en Analog til Digital converter (ADC). Microbitten forstår kun 0 og 1. 0 volt = 0 og 3 volt = 1, hvad så med alt det imellem. I vores tilfælde hvis vi ville måle lystet, ville vi kun vide om det var lyst eller mørkt, alt der imellem vil vi gå glip af. Så det er heldigt vi har en ADC som kan hjælpe os med at måle flere nuancer. Opløsningen (resolution på engelsk), altså hvor godt kan vi måle imellem 0 og 1 afhænger af hvor mange bit vores ADC er på. Som med alt andet jo bedre opløsning jo flere bit jo mere koster den. Microbitten har en opløsning på 10bit altså får vi 2^10 = 1024 step. En computer startet altid med at tælle fra 0, så 0 - 1023 giver 1024 step. [læs mere om ADC](https://learn.sparkfun.com/tutorials/analog-to-digital-conversion)

[Tilbage til toppen](#eksperimenter-med-lys-og-dataoptagelse)

# Tracking af dyr

For at følge et dyr i naturen og estimere dens position, kan man anvende Global Positioning System, det vi kender som [GPS](https://da.wikipedia.org/wiki/Global_Positioning_System).

![GPS](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/ConstellationGPS.gif)

Andre har udviklet en metode, som bruger optagelser af lyset styrke og tiden mellem solopgang og solnedgang for at afgøre positionen.

![tracking by light](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/Animal_lightLevel_tracking.png)

[Tilbage til toppen](#eksperimenter-med-lys-og-dataoptagelse)

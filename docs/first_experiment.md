## Første eksperiment
Vi starte med en simpel måling af lysniveauet i lokalet og skrive værdien på microbittens display når vi trykker på knap A
Til dette forsøg bruger vi microbittens eget display til at måle lysintensiteten, den kan kun give os et tal mellem 0 og 255 altså 256 step. Så den har ikke så god en opløsning som den ADC du kan læse om på [forsiden](https://hanshenrikjeppesen.github.io/Microbit_light_level/#hvorfor-1023).  

![microbit](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/microbit.jpg)

### Hvad skal vi bruge
Til dette forsøg skal vi kun bruge følgende ting.:
* En Notesbog
    * Det allervigtigste, en notesbog, det er altid vigtigt at have en laboratorienotesbog ved sin side når man laver forsøg. Herkan man hurtigt skrive nye ideer ned, eller huske på detaljer, *Hvornår startede jeg forsøget* *Hvor mange gange* osv..
* 1 x Micro:bit
* 1 x USB kabel
* 1 x Computer med internet og [Microsoft MakeCode](https://pxt.microbit.org/)

Vi skal slutte med at have følgende kode som skal overføres til microbitten:

![slut kode](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/blocks_light_level01.png)

## Lad os lad os bryde det ned i nogle step:

**Først skal vi have en inputknap, den trækker vi ud på vores skrivebord, vores codebord
![step01](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/ex01_step01.png)

**Herefter skal vi have en variabel som vi kan tildele en værdi. Variablen omdøber (rename) vi til lysniveau
![step02](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/ex01_step02.png)

**Nu vi har lavet vores variabel og kaldt den lysniveau, er vi klar til at give den en værdi. Under "Input" finder vi en block som hedder "light level"
![step03](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/ex01_step03.png)


![step04](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/ex01_step04.png)
![step05](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/ex01_step05.png)




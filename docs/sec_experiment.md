# Eksperiment nr. 2

Vi skal arbejde med at optage data over en periode, data vil vi gemme i en fil på microbitten og når optagelsen er færdig, vil vi hente den over på en computer og arbejde videre så vi kan visualisere vores data. Det kan vi gøre på den nemme eller den spændende måde, men mere om det senere. Koden til dette eksperiment skriver vi i programmeringssproget [MicroPython](https://micropython.org/) som er en adoption af hovedsproget Python version 3.x. [MicroPython](https://micropython.org/) er tilrettet således at det kan bruges på en microcontroller som fx. en Micro:bit.

Måde vi skriver vores koden på er lidt anderledes end hvad vi gjorde i det [første eksperiment](https://hanshenrikjeppesen.github.io/Microbit_light_level/docs/first_experiment.html). Her brugte vi et grafisk kodesprog Microsoft Blocks, nu vil vi bruge et tekst baseret kodesprog, her er et lille eksempel på noget af det kode vi skal skrive. 

### Hvad skal vi bruge:

Til vores eksperiment skal vi bruge lidt forskelligt og det kan selvfølgelig afhænge lidt af hvad man har til rådighed. Her er en liste over ting vi skal bruge:

* En notesbog til at holde styr på alt vores nye viden evt [en Rocketbook](https://getrocketbook.com/)
* 1 x BBC microbit
* 1 x Photosensor LDR (kan foreksempel købes [her](http://microbit-accessories.co.uk/shop/sensor/ldr-light-sensor/)
    * Har du et Inventors Kit fra Kitronik indeholder den en LDR [køb her](https://www.podconsultsbutik.dk/micro-bit-inventors-kit)
* 1 x batteripack
* 1 x USB kabel
* 1 x 10kohm Modstand
* 3 x kabler til forbindelse
   * Jumper wires hvis man anvender Inventors Kit
   * ellers krokodille kabler 

### Editors

Der er forskellige måder at skriver og overføre din MicroPython kode til microbitten, men vi vil tage udgangspunkt i de to nok mest benyttede metoder og vi vil lave et lille forsøg, som vil vise at det ikke er helt ligegyldig hvilken editor vi bruger.

#### 1
På [python.microbit.org](http://python.microbit.org/editor.html) finder vi en online editor. Her kan vi skrive vores kode, gemme vores kode **Save** som en .py fil. Vi kan **Download** en .hex fil som vi kan overføre til microbitten for at lægge vores program over på den.

![micropython editor](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/Micropython_editor.png)

#### 2

Editoren [Mu](https://codewith.mu/) er en rigtig fin og simpel editor og kan hentes og installers på Windows, OSX, Linux og Raspberry Pi.

![mu editor](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/mu_editor_screen.png)


### Vores forsøgsopsætning

Vi tager i første omgang udgangspunkt i Inventors Kit længere nede kan du finde opsætningen hvis man anvender photosensoren direkte med krokodille kabler:

![Billede af inventors kit](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/5603_inventors_kit_for_the_bbc_microbit_description.jpg)

![Opsætning af breadboard](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/experiment_light_breadboard.png)

Hvis du har købt en LDR hos [microbit-accessories](http://microbit-accessories.co.uk/shop/sensor/ldr-light-sensor/) vil din forsøgsopstilling se sådan her ud:

![Opsætning med LDR Clip_cabel](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/Microbit_with_LDR_clip.jpg)



```python
from microbit import *
import os

while True:
    if button_b.is_pressed():
        break
    else:
        display.show(Image.ARROW_E)
        

file = 'lightLevel.csv'

light = pin0.read_analog()
with open(file, 'w') as new_file:
    new_file.write(str(light) + ',')

reading = 0

while True:
    light = pin0.read_analog()
    
    with open(file, 'r') as data_file:
        content = data_file.read()
    
    newContent = content + str(light) + ','
    
    with open(file, 'w') as data_file:
        data_file.write(newContent)
    
    reading += 1
    display.set_pixel(2,2,5)
    sleep(50)
    display.clear()
    if reading == 250:
        break
        
    sleep(120000)
    
while True:
    sleep(5000)
    display.show('F')
    sleep(100)
    display.clear()
```

[forsiden](https://hanshenrikjeppesen.github.io/Microbit_light_level).

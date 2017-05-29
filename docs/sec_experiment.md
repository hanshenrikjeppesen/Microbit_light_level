# Eksperiment nr. 2

Vi skal arbejde med at optage data over en periode, data vil vi gemme i en fil på microbitten og når optagelsen er færdig, vil vi hente den over på en computer og arbejde videre så vi kan visualisere vores data. Det kan vi gøre på den nemme eller den spændende måde, men mere om det senere. Koden til dette eksperiment skriver vi i programmeringssproget [MicroPython](https://micropython.org/) som er en adoption af hovedsproget Python version 3.x. [MicroPython](https://micropython.org/) er tilrettet således at det kan bruges på en microcontroller som fx. en Micro:bit.

Måde vi skriver vores koden på er lidt anderledes end hvad vi gjorde i det [første eksperiment](https://hanshenrikjeppesen.github.io/Microbit_light_level/docs/first_experiment.md). Her brugte vi et grafisk kodesprog Microsoft Blocks, nu vil vi bruge et tekst baseret kodesprog, her er et lille eksempel på noget af det kode vi skal skrive. 

```python
from microbit import *

while True:
    if button_b.is_pressed():
        break
    else:
        display.show(Image.ARROW_E)
```

Til vores eksperiment skal vi bruge lidt forskelligt og det kan selvfølgelig afhænge lidt af hvad man har til rådighed. Her er en liste over ting vi skal bruge:

### Hvad skal vi bruge:

* 1 x BBC microbit
* 1 x Photosensor LDR (kan foreksempel købes [her](http://microbit-accessories.co.uk/shop/sensor/ldr-light-sensor/)
    * Har du et Inventors Kit fra Kitronik indeholder den en LDR [køb her](https://www.podconsultsbutik.dk/micro-bit-inventors-kit)
* 1 x batteripack
* 1 x USB kabel
* 1 x 10kohm Modstand
* 3 x kabler til forbindelse
   * Jumper wires hvis man anvender Inventors Kit
   * ellers krokodille kabler 

![Billede af inventors kit](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/5603_inventors_kit_for_the_bbc_microbit_description.jpg)

### Vores forsøgsopsætning

Vi tager i første omgang udgangspunkt i Inventors Kit længere nede kan du finde opsætningen hvis man anvender photosensoren direkte med krokodille kabler:

![Opsætning af breadboard](https://hanshenrikjeppesen.github.io/Microbit_light_level/IMAGE/experiment_light_breadboard.png)

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

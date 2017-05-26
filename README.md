# Eksperiment med Lys og data optagelse

Vi skal prøve at måle lysintensiteten som er i rummet omkring microbitten. Lys måles normalt i [LUX](https://da.wikipedia.org/wiki/Lux) som er [SI-enhed](https://da.wikipedia.org/wiki/Syst%C3%A8me_International_d%27Unit%C3%A9s) for måling af belysningsstyrke. I vores arbejde med microbitten bliver vores målinger oversat (translateret) til en analog strømstyrke. Denne strøm kan veksle mellem 0V og 3V. OV vil sige intet lys, og som i nok allerede har gættet 3V vil sige MEGET lys. Microbitten omdanner den målte værdi til et tal mellem 0 og 1023 (Hvorfor 1023 ??)

Vores målinger kan vi bruge til mange forskellig opgaver, foreksempel:
* En alarm som ringer når nogen tænder lyset på dit værelse
* Tænde udendørslys når det bliver for mørkt
* Tilpasse lysniveau i et rum efter narturligt lys som kommer ind i rummet
* Lave et diagram over solen som står op

[link](/docs/newPage.md)
Vi kan måle lysniveauet på forskellige måder, så lad os bare komme i med en simpel måde:

## Første eksperiment
Vi starte med en simpel måling af lysniveauet i lokalet og skrive værdien på microbittens display når vi trykker på knap A

### Hvad skal vi bruge
Til dette forsøg skal vi kun bruge 2 ting.:
* En Notesbog
    * Det allervigtigste, en notesbog, det er altid vigtigt at have en laboratorienotesbog ved sin side når man laver forsøg. Herkan man hurtigt skrive nye ideer ned, eller huske på detaljer, *Hvornår startede jeg forsøget* *Hvor mange gange* osv..
* 1 x Micro:bit


Vi skal arbejde med at optage data over en periode, data vil vi gemme i en fil på microbitten og når optagelsen er færdig, vil vi hente den over på en computer og arbejde videre med den så vi kan visualisere vores data.

Til vores eksperiment skal vi bruge lidt forskelligt og det kan selvfølgelig afhænge lidt af hvad man har til rådighed. Her er en liste over ting vi skal bruge:

{% highlight Python linenos %}
from microbit import *

while True:
    if button_b.is_pressed():
        break
    else:
        display.show(Image.ARROW_E)
        
{% endhighlight %}

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

![Billede af inventors kit](/IMAGE/5603_inventors_kit_for_the_bbc_microbit_description.jpg)

### Vores forsøgsopsætning

Vi tager i første omgang udgangspunkt i Inventors Kit længere nede kan du finde opsætningen hvis man anvender photosensoren direkte med krokodille kabler:

![Opsætning af breadboard](/IMAGE/experiment_light_breadboard.png)

   

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for
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
```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/hanshenrikjeppesen/Microbit_light_level/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

# CleanPort

Una solució integral per a la detecció i gestió de la contaminació marina

## Sensors

Cada punt de mesura estarà composat de dues parts fonamentals:

### Sensor de presència d’hidrocarburs sense contacte

El sensor que s’utilitzarà és el ROW Oil Spill Sensor. S’ha escollit aquest sistema concretament per la seva qualitat i el fet que està dissenyat específicament per a aquest fi: es podrà evitar falsos positius causats per brutícia gràcies al seu sistema làser que només excita hidrocarburs i es reduirà l’efecte de la mar degut al contenidor inoxidable que té.

A més a més, s’ha utilitzat en múltiples solucions anteriors amb èxit.
![imatge node](https://raw.githubusercontent.com/oriolgalceran/cleanport/master/768x590-falcon-compressed.png)

### Node de sensors IoT

La comunicació de tota la xarxa es durà a terme mitjançant l’estàndard de comunicacions per ràdio LoRaWAN, que permetrà facilitar enormement la instal·lació i minimitzar la infraestructura de comunicació necessària per transmetre les dades.

Cada sensor necessitarà un node de comunicació que llegeixi les dades i les envii a la gateway central. Aquest node, a l’estar a prop del mar, requereix protecció contra els elements. En aquest cas utilitzarem un node de l’empresa Digital Matter que disposa de protecció IP67.

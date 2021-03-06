# CleanPort

Una solució integral per a la detecció i gestió de la contaminació marina.

## Sensors

Cada punt de mesura està composat de dues parts fonamentals:

### Sensor de presència d’hidrocarburs sense contacte

El sensor que s’utilitza és el ROW Oil Spill Sensor de Laser Diagnostic Instruments. S’ha escollit aquest sistema concretament per la seva qualitat i el fet que està dissenyat específicament per a aquest fi: pot evitar falsos positius causats per brutícia gràcies al seu sistema làser que només excita hidrocarburs i es redueix l’efecte de la mar degut al contenidor inoxidable que té.

![imatge node](https://github.com/oriolgalceran/cleanport/blob/master/row.png)

A més a més, s’ha utilitzat en múltiples solucions anteriors amb èxit.

![prova1](https://github.com/oriolgalceran/cleanport/blob/master/row1.PNG)
![prova1](https://github.com/oriolgalceran/cleanport/blob/master/row2.PNG)
![prova1](https://github.com/oriolgalceran/cleanport/blob/master/row3.PNG)

### Node de sensors IoT

La comunicació de tota la xarxa es duu a terme mitjançant l’estàndard de comunicacions per ràdio LoRaWAN, que permet facilitar enormement la instal·lació i minimitzar la infraestructura de comunicació necessària per transmetre les dades.

Cada sensor necessita un node de comunicació per llegir les dades i enviar-les al Gateway. Aquest node, a l’estar a prop del mar, requereix protecció contra els elements. En aquest cas s'utilitza el node LoRaWAN de l’empresa Digital Matter que disposa de protecció IP67.

![imatge node](https://raw.githubusercontent.com/oriolgalceran/cleanport/master/768x590-falcon-compressed.png)

### Alimentació
Tot i que el sistema no requereix d'una connexió física de dades, sí que necessita corrent, i per tant s'haurà d'utilitzar la xarxa elèctrica del Port. En el cas de que la localització del sensor no ho permeti, o resulti massa costós dur-ho a terme, l'empresa comercialitzadora del sensor també disposa de versions amb plaques solars i bateries, fet que asseguraria un funcionament permanent amb un manteniment mínim.

## Gateway LoRaWAN

L’altíssim rang de transmissió d’aquest protocol ens permet utilitzar **només un Gateway per a tot el Port**, des del Port Vell fins a la Zona Franca. En el cas de voler redundància, se’n podrien instal·lar dos, un a la zona del Port Vell i l’altre al Moll de l’Energia.

La funció d’aquest Gateway és reunir les dades de tots els sensors i redirigir-les cap al sistema de monitorització. S’utilitza la Gateway de Nordic Automation Systems. Els punts a favor d’aquest producte en concret són la seva construcció robusta per a exteriors i la seva versatilitat a nivell de connexions, que permet utilitzar 4G en cas de que Ethernet no estigui disponible.

Per una infraestructura amb ambicions de lideratge en el món de l’IoT, establir una xarxa d’aquest tipus és pràcticament una obligació, ja que els seus usos no s’acaben aquí: resultarà una eina imprescindible per futurs projectes al Port. Per exemple, sense sortir d’aquest mateix cas, es podria fàcilment instal·lar una sèrie de trackers GPS als vehicles i embarcacions de lluita per conèixer exactament on són durant un esdeveniment de contaminació i poder respondre efectivament a les necessitats del moment. Els beneficis no s’acaben aquí: en el cas de que es volgués fer una altra instal·lació no caldria utilitzar cap tipus de cable o pagar accés a xarxes cel·lulars perquè el Port disposaria d’una xarxa independent de comunicació immune a factors externs. Altres aplicacions serien una xarxa de control meteorològic, comptadors de persones, tracking de mercaderies, assistència a la Policia Portuària, gestió d’incidències...

![gateway](https://github.com/oriolgalceran/cleanport/blob/master/lorawan_gateway_IX1001_3.png)

## Sistema de monitorització

El sistema de monitorització té una part de back-end i una part de front-end.

El back-end consisteix en un servidor que rep les dades i les guarda en una base de dades per poder revisar posteriorment les alarmes i que publica un arxiu JSON amb les últimes dades. 

El front-end consisteix en un lloc web d’accés privat (o a la intranet del Port) que permet al personal del Port veure en directe l’estat de tots els sensors sobre un mapa. En el cas de que hi hagi una detecció, es pot procedir a emetre avisos de moltes formes, ja sigui mitjançant SMS a números predefinits, avisos a pantalla, avisos per correu electrònic…

Les dades del web actualment són una simulació ja que les dades ara mateix no estan disponibles.

El lloc web està disponible a https://oriolgalceran.github.io/cleanport . També funciona perfectament en dispositius mòbils.

## Validació

Partint de que el sensor escollit detecta exclusivament la presència d’hidrocarburs i que és calibrable, és poc probable que hi hagin falses alarmes. Degut a la versatilitat del sistema de monitorització, quan salti una alarma es pot enviar un missatge SMS a l’encarregat de la zona més propera al sensor perquè ho comprovi immediatament. Per tant, creiem que el sistema de validació remot més adequat és utilitzar la xarxa de càmeres del Port, afegint-ne als llocs on no hi hagi visió, i invertint en càmeres d'alt rendiment per cobrir grans zones del front marítim.

El sistema de monitorització pot associar una càmera a cada sensor i mostrar les seves imatges en el moment de detectar una alarma.

Altres propostes, com per exemple drons autònoms, són inviables degut a la condició del Port com a infraestructura crítica en moviment constant. Per molt avançats que siguin aquests sistemes, no es pot assumir el risc de que un dron impacti contra una embarcació o un vehicle industrial o comercial i els requeriments econòmics de la infraestructura necessària no la justifiquen.

## Cost

L'arquitectura en xarxa d'aquesta solució permet aconseguir uns costos reduïts tot superant els objectius amb escreix, ja que no requereix de la instal·lació de cables i permet la connexió de molts sensors (de diversos tipus) a una sola centraleta. A més, aquesta mateixa versatilitat permet l'ús de més o menys estacions de control, seleccionades segons les necessitats particulars del Port.



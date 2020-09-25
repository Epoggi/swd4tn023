## Sisällysluettelo

# Johdanto koneoppimiseen

Koneoppimisessa on kyse siitä, että datan avulla tietokone voidaan opettaa ratkaisemaan ongelmia tietyssä toimintaympäristössä ilman varsinaista ohjelmointia. Dataa kyseisestä ongelmakentästä täytyy kuitenkin olla paljon, jotta *koneoppimismalli* voidaan kouluttaa. Ongelmakentän tulee myös olla tarkasti rajattu, eikä samalla datalla koulutettua mallia voida siirtää toisen ongelman ratkaisuun. Termiä *tekoäly* tunnutaan käyttävän monesti myös synonyyminä koneoppimisesta ja toisaalta mikä tahansa tavallinen ohjelmoitu algoritmi saatetaan nykyään luokitella valtamediassa "tekoälyksi". 

Yksinkertaisia ongelmia voi mallintaa lineaarisilla funktioilla. Kerätyn datan perusteella, voimme laskea lineaariselle *tavoitefunktiolle (objective function)* painokertoimet ja tehdä ennusteen uudelle datapisteelle. 
![lineaarinen tavoitefunktio](img/lineaarinen_tavoitefunktio.png)

Usein reaalimaailman asiat ja ilmiöt ovat sen verran monimutkaisia, että lineaarinen ennustemalli olisi hyvin epätarkka. Tällöin voidaan käyttää sen sijaan epälineaarista tavoitefunktiota.
![epälineaarinen tavoitefunktio](img/epalineaarinen_tavoitefunktio.png)

Edelliset ennustemallit ovat vielä ihmiselle helposti ymmärrettäviä. Kuitenkin vielä epälineaarisia ennustemalleja parempi on yleensä neuroverkkoihin pohjautuva ennustemalli. Neuroverkkoa voi ajatella samanlaisena (mutta monimutkaisena) matemaattisena funktiona, jossa on painokertoimet kuten lineaarisessa ja epälineaarisessa tavoitefunktiossa. Neuroverkoissa painokertointen määrittäminen vain on korkeamman asteen matematiikkaa. Tämä matemaattinen mallinnustapa on saanut inspiraationsa ihmisaivojen neuroverkoista, jotka aktivoituvat (painottuvat) niiden käytön mukaan. Neuroverkkojen yhteydessä puhutaan myös syväoppimisesta (deep learning), mikä viittaa neuroverkon kerrosten syvyyteen. Neuroverkkoja voi käyttää varsin sujuvasti ymmärtämättä niiden tarkkaa matemaattista toteutusta. Kuitenkin neuroverkkojen toimintaa (ja mallin hyvyyttä) säädetään ns. *hyperparametrien* avulla, joiden tehokas käyttö edellyttää jonkin verran ymmärrystä neuroverkkojen toiminnasta.
![neuroverkko](img/neuroverkko.png) 

## Miten kone oppii

![koneoppimisen tavat](img/koneoppimisen_tavat.png) 

Koneen opettamiseen on kolme erilaista tapaa, **ohjattu oppiminen, ohjaamaton oppiminen ja vahvistusoppiminen**. Eri tavat soveltuvat erikaltaisten ongelmien ratkaisemiseen.  

**Ohjatussa oppimisessa (supervised learning)** annamme koneelle ison joukon *merkittyä dataa (labelled data)*. Konelle voidaan siis antaa esimerkiksi 1000 kuvaa, joissa esiintyy kissa (tai rikkoutunut putki tai syöpäkasvaimen esivaihe). Tai koneelle voidaan antaa lauseita, joiden on luokiteltu sisältävän vaikka 50% "politiikkaa" ja 30% "luonnonsuojelua". Datan merkitseminen pitää tyypillisesti tehdä manuaalisena käsityönä. Kun kone on siis ajanut esimerkiksi 1000 kissakuvaa neuroverkkoon, niin se osaa tämän rakentamansa *mallin* avulla tunnistaa esiintyykö jossain tuntemattomassa kuvassa kissa. Koulutuksen aikana voidaan säätää mallin *hyperparametereja*, jotka vaikuttavat siitä kuinka hyvä mallista tulee. (Tekoäly bisneksen uudet työkalut, 2019).

**Ohjaamattomassa oppimisessa (unsupervised learning)** koneelle annetaan vain joukko dataa ja koneen annetaan itse tunnistaa datasta samankaltaisuuksia ja jakaa data joukkoihin. Mallin *hyperparametreja* säätämällä kone saadaan painottamaan datan luokittelussa erilaisia asioita. Ohjaamattoman oppimisen hyvä puoli on se, ettei dataa tarvitse luokitella itse, mutta toisaalta ohjaamaton oppiminen soveltuu vain rajattuihin ongelmiin, kuten poikkeavuuksien löytämiseen, asiakaryhmien luokitteluun jne. Ohjaamattoman oppimisen eräs mielenkiintoinen sovellutus on *K-Nearest Neighbours-algoritmiin* perustuva suosittelu. Jos esimerkiksi verkkokaupan asiakkaat on luokiteltu erilaisiin ryhmiin, niin uusi asiakas voidaan hänen käyttäytymisensä perusteella luokitella kuuluvaksi tiettyyn ryhmään ja suositella hänelle esimerkiksi samoja tuotteita, joita muut sen ryhmän asiakkaat ovat ostaneet. (Tekoäly bisneksen uudet työkalut, 2019).

![Ohjaamaton oppiminen](img/ohjaamaton_oppiminen.png) 

Ohjattu ja ohjaamaton oppiminen toimivat siis alla olevassa kuvassa esitettyjen vaiheiden mukaisesti.
![koneoppimisen vaiheet](img/koneoppimisen_vaiheet.png) 

**Vahvistusoppimisessa (reinforcement learning)** koneen annetaan itse kokeilla ja tehdä virheitä "keppi ja porkkana"-mallilla. Vahvistusoppimista varten rakennetaan simulaatioympäristö, jossa koneelle annetaan pisteitä sen toiminnasta. Vahvistusoppiminen toimii hyvin esimerkiksi erilaisten pelien, vaikkapa shakin, kouluttamisessa. Tietokone voi pelata miljoonia pelejä itseään vastaan ja "simulaatioympäristö" antaa palautetta yksinkertaisimmillaan vain siitä, voittiko kone pelin. Monessa oikean maailman ongelmassa palautesykli koneen tekemien valintojen ja onnistumisen välillä voi olla hyvin pitkä (helposti vaikka useita viikkoja), jolloin kone oppii hyvin hitaasti. Samaten simulaatioympäristön rakentaminen voi olla haastavaa. Käytännön maailmassa itseajavia autoja pyritään kouluttamaan vahvistusoppimisen avulla. Ihminen voi siis esimerkiksi istua auton kyydissä ja antaa jatkuvasti pisteitä koneen tekemistä valinnoista.

![koneoppimisen vaiheet](img/vahvistusoppiminen.png) 

## Koneoppiminen käytännössä
<!--
Koneoppimiseen liitty useita kirjastoja ja työkaluja, joilla kaikilla on oma roolinsa koneoppimismallien rakentamisessa ja havainnollistamisessa.

Jupyter on..
TensorFlow on kirjasto *moniulotteisten taulukoiden (~tensoreiden)* käsittelyyn eli tensorilaskentaan. TensorFlown *operaatioilla* (esim tf.add()) voidaan muokata tensoreita. Tensorit kulkevat *graafien* läpi, jotka muokkaavat tensoreita operaatioilla. Usein edellisen operaation läpikäyneestä ulostulo-tensorista tulee seuraavaan operaation sisäänmeno-tensori. Graafit tulee ajaa TensorFlow *sessiossa*, joskin TensorFlow 2:ssa ei enää (https://www.tensorflow.org/guide/effective_tf2). TensorFlown käsitteiden ja käytön opettelu vaatii hieman aikaa. (https://colab.research.google.com/notebooks/mlcc/tensorflow_programming_concepts.ipynb). 
Pandas (Panda on työkalu erityisesti kolumni-muotoisen datan käsittelyyn. Pandas:lla voi ladata dataa (esim CSV-tiedostoista) ja esittää sitä myös graafeina).
Numpy (https://numpy.org/) Kirjaston numeroiden käsittelyyn Pythonilla.
sklearn Metriikoiden laskemiseen ja tulostamiseen datasta.
matplotlib Kirjasto datasettien visualisointiin.
Keras

Ibm Watson

Koneoppimiskirjastojen rajapinnat eivät ole vielä valitettavasti kehittyneet aivan yhtä korkealle abstraktiotasolle (ja helppokäyttöisiksi) kuin esimerkikiksi webohjelmointiin liittyvät kirjastot. Kuten muussakin ohjelmoinnissa, hyvä tapa lähteä liikkeelle koneoppimismallien rakentamisessa on pyrkiä etsimään esimerkki, joka tekee melkein saman asian jota itse yrittää tehdä ja sitten muokata esimerkkiä omiin tarpeisiin sopivaksi.

-->
<!---käytetään tällä kurssilla (ainakin ennen seminaaria) googlen colab online-ympäristöä ja esimerkkejä sieltä-->


<!--(käydään läpi työkalustack ja eri työkalujen erot, jotka voitaisiin asentaa itselle condalla, ks blogi) Keras, tensorflow, jupyter, pandas, numpy, ibm watson, kuten esim https://medium.com/@margaretmz/anaconda-jupyter-notebook-tensorflow-and-keras-b91f381405f8-->

<!---tensorit selitetään (moniulotteinen taulukko)-->


## Tehtävät

### Lähteet:
* Kananen H., Puolitaival H., Tekoäly bisneksen uudet työkalut, Alma Talent, 2019.
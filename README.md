# Staðfangaskrá EXTRA
## Vikulega uppfærð, auðguð, útgáfa af Staðfangaskrá Þjóðskrár

---

Hér má nálgast auðgaða útgáfu af staðfangaskrá. Í stuttu máli:

* Einungis staðföng í Reykjavík
* Uppfært vikulega
* Aukin eigindi koma frá svæðaskiptingum LUKR
* Auðvelt að bæta við eigindum ef flákar/svæðaskiptingar eru fyrir hendi

### Tæknilýsing

Kl. 22:15 hvert sunnudagskvöld keyrir CircleCI eftir skilgreiningum í `.circleci/general.yml`

Fyrst eru hráskrár sóttar. Það eru annarsvegar .geojson skrár með flákum ýmissa skiptinga sem eru sóttar frá LUKR og hinsvegar staðfangaskráin sjálf. 

Sá kóði býr í `fetch_sources.py`. Skilgreiningar fyrir hráskrárnar eru í `config.py`.  Hráskrárnar eru geymdar í `sources/` möppunni

Því næst keyrir `new_stadfangaskra.py`. Þar er eigindum bætt við hvert staðfang ef það fellur inn í flákana. 

Tökum dæmi um staðfangið með HEINUM 10135437 (Borgartún 8-16A). Svona lítur það út í staðfangaskrá:

|Eigindi             | Gildi               |  
|--------------------|---------------------|
| HNITNUM            | 10017780            |
| SVFNR              | 0000                |
| BYGGD              | 01                  |
| LANDNR             | 199350              |
| HEINUM             | 1112740             |
| FASTEIGNAHEITI     | Borgartún 8\-16A    |
| MATSNR             |                     |
| POSTNR             | 105                 |
| HEITI\_NF          | Borgartún           |
| HEITI\_TGF         | Borgartúni          |
| HUSNR              | 8                   |
| BOKST              | A                   |
| VIDSK              | 8\-16               |
| SERHEITI           |                     |
| DAGS\_INN          | 2007\-09\-07        |
| DAGS\_LEIDR        | 2013\-12\-10        |
| GAGNA\_EIGN        | Þjóðskrá Íslands    |
| TEGHNIT            | 0                   |
| YFIRFARID          | 0                   |
| ATHUGASEMD         |                     |
| NAKV\_XY           |                     |
| X\_ISN93           | 358474\.193181818   |
| Y\_ISN93           | 407951\.068181818   |
| LAT\_WGS84         | 64\.1450988589666   |
| LONG\_WGS84        | \-21\.9083489552494 |
| DAGS\_UTGAFA       | 2020\-09\-13        |


Skráin `output/stafangaskra_exta.csv` inniheldur auk þessara eiginda, eftirfarandi eigindi, sem er bætt við sjálfkrafa:

| Eigindi                         | Gildi            |
|---------------------------------|------------------|
| LUKR\_SKOLI\_YNGRI\_STIG        | Austurbæjarskóli |
| LUKR\_SKOLI\_UNGLINGA\_STIG     | Austurbæjarskóli |
| LUKR\_SKOLI\_SKOLANR            | 4                |
| LUKR\_SORPHIRDA\_BILL           | 4\.1             |
| LUKR\_STJORNSYSLUHVERFI\_HVERFI | 4\. Laugardalur  |
| LUKR\_HVERFAHEITI\_HEITI        | Tún              |

Auk þess eru í `output`möppunni útgáfur sem innihalda einungis eigindi frá tilteknum svæðaskiptingum. Þar er t.d. `skolahverfi.csv`, sem inniheldur þá einungis eigindi sem tengjast skólahverfum, en ekki öðrum svæðaskiptingum.

Öll viðbættu eigindi hafa (að þessu sinni) forskeytið LUKR.

---


### Hvað er staðfangaskrá?

```
Staðfang (e. Access address) geymir bæði lýsandi og rúmfræðilegar upplýsingar um staðsetningu. 
Með lýsandi upplýsingum er til að mynda átt við í hvaða sveitarfélagi, bæ eða hverfi staðfangið er og við hvaða götu. 
Með rúmfræðilegum upplýsingum er átt við tvívítt hnit í samræmdu landshnitakerfi.

Staðföng nýtast þannig við skráningu einstaklinga, fyrirtækja, landeigna, mannvirkja, svæða eða annars sem þörf er á. 
Staðföng gagnast því almenningi með beinum hætti, sem og í gegnum hinar ýmsu stofnanir og fyrirtæki, 
svo sem stjórnvöld, neyðarþjónustu, rannsóknaraðila, veitufyrirtæki og fleiri.  

Í grunninn er staðfang áfangastaður. Það vísar á inngang mannvirkis eða annars konar aðkomu. 
Tengslum staðfanga og landeigna er þannig háttað að mörg staðföng geta verið tengd hverri landeign 
en aðeins ein landeign er tengd hverju staðfangi. Þannig getur t.d. hver stigagangur fjölbýlishúss átt sitt staðfang. 
```

Reglugerð um skráningu staðfanga má finna [hér](https://www.reglugerd.is/reglugerdir/eftir-raduneytum/srn/nr/0577-2017). 

Staðfangaskrá Þjóðskrár má sækja [hér](https://skra.is/thjonusta/gogn/hra-gogn/)

---

### Eigindi staðfangaskrár

Eigindi staðfangaskrár eru þessi:

| Eigindi        | Lýsing                                                                                                                                         |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| HNITNR         | Hlaupandi upplýsingalaust auðkennisnúmer staðfangs\. Hvert staðfang getur verið tengt mörgum hnitum, en hvert hnit hefur aðeins eitt hnitnúmer |
| SVFN           | Sveitarfélagsnúmer er fjögurra stafa auðkennisnúmer                                                                                            |
| BYGGD          | Byggðarnúmer innan viðkomandi sveitarfélags                                                                                                    |
| LANDNR         | Hlaupandi sex stafa auðkennisnúmer landeigna í landeignaskrá Þjóðskrár Íslands                                                                 |
| HEINUM         | Heitinúmer er sjö stafa auðkennisnúmer staðfanga/fasteignaheita\. Eitt heitinúmer er fyrir hvert staðfang                                      |
| FASTEIGNAHEITI | Heiti fasteignar í Þjóðskrá Íslands\. Skráð af viðkomandi sveitarfélagi                                                                        |
| MATSNR         | Matsnúmer \(7 stafir\)\. Raðnúmer\. Sérhver matseining er auðkennd með matsnúmeri\.                                                            |
| POSTNR         | Póstnúmer þess póstsvæðis sem staðfang er innan skv\. nýjustu upplýsingum frá Íslandspósti hf\.                                                |
| HEITI\_NF      | Staðfang í nefnifalli                                                                                                                          |
| HEITI\_TGF     | Staðfang í þágufalli                                                                                                                           |
| HUSNR          | Húsnúmer                                                                                                                                       |
| BOKST          | Viðbættur bókstafur                                                                                                                            |
| VIDSK          | Viðskeyti við staðfang                                                                                                                         |
| SERHEITI       | Sérheiti staðfangs                                                                                                                             |
| DAGS\_INN      | Dagsetning fyrstu innskráningar                                                                                                                |
| DAGS\_LEIDR    | Dagsetning síðustu leiðréttingar                                                                                                               |
| GAGNA\_EIGN    | Þjóðskrá Íslands er eigandi staðfangaskrár                                                                                                     |
| TEG\_HNIT      | Tegund hnits                                                                                                                                   |
|                | 0 Eftir að yfirfara tegund hnits                                                                                                               |
|                | 1 Áætlaður miðpunktur mannvirkis                                                                                                               |
|                | 2 Staðsetning megin inngangs í mannvirki                                                                                                       |
|                | 3 Hnitpunktur staðsettur á innkeyrslu lóðar                                                                                                    |
|                | 4 Hnitpunktur staðsettur með vissu innan lóðamarka                                                                                             |
|                | 5 Hnitpunktur staðsettur innan áætlaðs byggingarreits                                                                                          |
| STADA          | Staða hnits0Óyfirfarið1Yfirfarið2Þarf endurskoðun9Vantar heitinúmer                                                                            |
| ATHUGASEMD     | Notað til ítarlegri aðgreiningar t\.d\. á matshlutum og skráningu heimildarmanna eða heimilda                                                  |
| X\_ISN93       | x\-gildi í austur mælt í metrum í ISN93                                                                                                        |
| Y\_ISN93       | y\-gildi í norður mælt í metrum í ISN93                                                                                                        |
| LAT\_WGS84     | Breiddargráða \(Norður\)                                                                                                                       |
| LONG\_WGS84    | Lengdargráða \(Austur\)                                                                                                                        |
| DAGS\_UTGAFA   | Dagsetning útskriftar skrár                                                                                                                    |
|                |                                                                                                                                                |





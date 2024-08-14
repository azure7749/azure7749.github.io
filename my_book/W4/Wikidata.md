# Wikidata Assignment
### [Wikidata: The Making Of](https://dl.acm.org/doi/pdf/10.1145/3543873.3585579)
The creation of wikidata...

### Contribution
![](https://imgur.com/QeDXbsq.jpg)

### Wikidata Query Service: Application
#### Description
利用wikidata query service來檢索全國村里列表並附上人口及所屬行政區等資訊
#### _Input_
```
SELECT ?village ?villageLabel ?population ?administrativeRegion ?administrativeRegionLabel ?city ?cityLabel WHERE {
  ?village wdt:P31 wd:Q7930614;        # Instance of village
           wdt:P17 wd:Q865;           # Located in Taiwan
           wdt:P1082 ?population.    # Population

  ?village wdt:P131 ?administrativeRegion.
  
  ?administrativeRegion wdt:P131 ?city.
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "zh-tw". }
}
ORDER BY DESC(?population)
```
#### _Results_
![](https://imgur.com/dY4AI9D.jpg)

#### Issues
如台北縣及台中縣等舊行政區資訊會一併顯示於結果中



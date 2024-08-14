# Wikidata Assignment
### [Wikidata: The Making Of](https://dl.acm.org/doi/pdf/10.1145/3543873.3585579)
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
直接以台灣的行政區來搜尋會出現已經廢除的台北縣 台中縣等資料
經更新query後可成供過濾
但若過濾台北縣則會一併過濾如過去為北縣行政區的台北市行政區（台北縣北投鎮，內湖鄉等）


                                                                           Realisé par  :   ELOUAHDANI Omar GLSID2
## XML extensible Markup Language 

# TP  xpath xml


1.	Les pays de plus de 6000000 habitants : 

       *  //country[population>6000000]/name

2.	Codes des pays bordant la France

       * //country[name="France"]/border


3.	Nombre de provinces en France ?

       * //country[name="France"]/count(province)

4.	Caractéristiques de Paris ?

       * //city[name="Paris"]

5.	Le nom et la population de la 3ème ville de France dans l'ordre du document.

       * //country[@car_code="F"]//city[3]
       * //country[@car_code="F"]//city[3]/(name,population[last()])


6.	Toutes les religions, sans doublons.


       * distinct-values(//country/province)


7.	 Noms des pays bordant la France
   
       * //country[name="France"]/border/@country

8.	les pays frontaliers communs à l'Allemagne et à la France.


       *  for $a in doc("mondial.xml")//country[@car_code="D"]/border/@country
       *  for $f in doc("mondial.xml")//country[@car_code="F"]/border/@country
       *  where $a=$f return data($f)


9.	Combien de fois la superficie de la France fait celle du Luxenbourg ?


       * let $a:=doc("mondial.xml")//country[name="France"]/@area let $b:=doc("mondial.xml")//country[name="Luxembourg"]/@area return $a div $b


10.	Quelle est la superficie de l'Europe ?


       * sum(//country[encompassed[@continent="europe"]]/@area)


11.	 Quel est la population de l’Afrique ?


       * sum(//country[encompassed[@continent="africa"]]/population[last()])


12.	Combien de pays a-t-on en afrique ?


       * count(//country[encompassed[@continent="africa"]])


13.	Quel sont les pays traversés par le Mississippi? 


       * //river[name="Mississippi"]/@country


14.	Quel sont les pays qui bordent France ?? 


       * //country[name="France"]/border/@country
     
     
15.	Combien et quels sont les pays qui E à plus d’un continent ? 

       * //country[count(encompassed)>1]/name

16.	 Quels sont les pays limitrophes de l’Allemagne ? 

       * //country[name="Germany"]/border/@country


17.	Quel est le pays ou la population est la plus dense ?

       *  //country[population[last()]=max(//country/population[last()])]

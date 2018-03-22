# jsonHtml  

    Format ultra simple d'un JSOM pour communiquer un html  
    
### Projet 

jsonHtml décrit un format de contenu JSON que l'on peut décoder en donnée HTML.
A l'origine, ce format à été élaboré dans le projet [toDomHtml](https://github.com/Prismalide/toDomHtml) avec lequel il est compatible. 
Son décodage et écriture ce veut très simple.
Des sources utiles sont disponibles:
[jsonHtml.js](js/src/) est l’implémentation en javascript.    

### version/licence
Format en version `Alpha` actuellement sous licence BSD 3
Source implèmentation  en version `Alpha` actuellement sous licence BSD 3
## Format minimaliste
Un jsonHtml est un tableau:   
**[ { tagName:...attributs... } , inner-1, ... , inner-n ]**     
Un jsonHtml est **récursif**. Ce qui veut dire que chaque **inner-x** peut être un jsonHtml.   

Le premier élément de l'array permet de déclarer le tag avec ses attributs.  
Plusieurs manières d'écrire:  
**{tagname:''}** => que tagname pas d'attributs  
**{tagname:'attributs déclarés en string'}** => tagname et d'attributs  
**{tagname:{maclass1:{maclass2-etc:'autres attributs'}}}** => tagName et x-class et/ou attributs.   
**{tagname:'', unattribut:'values',...}** => tagname et d'attributs individuels  
et tous les mélanges possibles:  
**{tagname:{maclass1:{maclass2-etc:'autres attributs', unattribut:'values',..., n_attribut:'values'}}}**   

## demo  
[first test.html](src/use/samples/)  

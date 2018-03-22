# jsonHtml  

    Format ultra simple d'un JSOM pour communiquer un html  
    
### Projet 
Ce projet est un extrait du projet [tplResource.](https://github.com/Prismalide/tplResource)  
Voici sa courte description et son convertisseur `très simple` en javascript.   

### version/licence
Actuellement en version `Alpha` sous licence BSD 2
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

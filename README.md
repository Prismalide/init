# jsonHtml  

    Format ultra simple d'un JSOM pour communiquer un html  
    
### Projet  

jsonHtml décrit un format de contenu JSON que l'on peut décoder en donnée HTML.   
A l'origine, ce format à été élaboré dans le projet [toDomHtml](https://github.com/Prismalide/toDomHtml) avec lequel il est compatible.   
Son décodage et écriture ce veut très simple.   
L'écriture d'un jsonHtml doit être proche de celle d'un html aussi bien en poid qu'en compréhension.
Des sources utiles sont disponibles:   
[jsonHtml.js](js/) est l’implémentation en javascript.    

### version/licence
Format en version `Alpha` actuellement sous licence BSD 3.   
Source implèmentation  en version `Alpha` actuellement sous licence BSD 3.   
Pour info vous trouverez [ici](JSON%20License.md) la licence de JSON.    
## Format minimaliste
jsonHtml est avant tout un json dont le contenu est préformaté.
Toute fois un parseur jsonHtml accepte certaines simplifications (identique au littéraux javascript). Les double guillemets peuvent-être remplacées par des simples et même être omises pour les noms de membres.     

Un jsonHtml ce présente sous la forme d'un tableau:   
**[ { tagName:...attributs... } , inner-1, ... , inner-n ]**     

Un jsonHtml est **récursif**. Ce qui veut dire que chaque **inner-x** peut être un jsonHtml.   

Le premier élément du tableau permet de déclarer le tag avec ses attributs.  
Plusieurs manières d'écrire:  
**{tagname:''}** => que tagname pas d'attributs  
**{tagname:'attributs déclarés en string'}** => tagname et d'attributs  
**{tagname:{maclass1:{maclass2-etc:'autres attributs'}}}** => tagName et x-class et/ou attributs.   
**{tagname:'', unattribut:'values',...}** => tagname et d'attributs individuels  
et tous les mélanges possibles:  
**{tagname:{maclass1:{maclass2-etc:'autres attributs', unattribut:'values',..., n_attribut:'values'}}}** 

## exemples:
Les exemples suivant montre que globalement l'écriture est aussi lourde en html que en jsonHtml
en jsonHtml:
```javascript
[{div:''},
	[{div:''},
	    "inner dans div",,
	    [{b:''},[{span:'style="..."' },[{i:''},[{u:''},[{em:''},"aprés br texte "]]], " suite après b.span.u.e "
	]]],
	"suite aprés div",
	[{hr:''}],
	,
	[{span:''},
	    "test span",
	    [{div:'style="..."' },
		"div dans span",
	]],[{div:''},
	    "suite dans div après span"
]]
```
donne en Html formaté:
```html
<div>
	<div>
		inner dans div<br />
		<b><span style="..."><i><u><em>aprés br texte </em></u></i> suite après b.span.u.e 
	</span></b></div>
	suite aprés div
	<hr />
	<br />
	<span>
		test span
		<div style="...">
			div dans span
	</div></span><div>
		suite dans div après span
</div></div>
```
avec class et id : 
```javascript
[{div:""},
	[{div:{class1:{class2:""}}}],
	[{div:"",id:"monId"}],
	[{div:{class2:{class1:""}},id:"monId2"}]
]
```
donne en Html formaté:
```html
<div>
	<div class="class1 class2 " ></div>
	<div id="monId" ></div>
	<div id="monId2" class="class2 class1 " ></div>
</div>
```	

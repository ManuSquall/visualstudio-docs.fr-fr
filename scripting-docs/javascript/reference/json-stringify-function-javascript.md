---
title: JSON.stringify, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: stringify method
ms.assetid: 0fafaf3b-c29b-46dc-b65b-ca223064a1d0
caps.latest.revision: "40"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3539bb003ed20a3ff7586e42466bf7c47165b83f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsonstringify-function-javascript"></a>JSON.stringify, fonction (JavaScript)
Convertit une valeur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] en chaîne JSON (JavaScript Object Notation).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
JSON.stringify(  
value [, replacer] [, space])  
```  
  
## <a name="parameters"></a>Paramètres  
 `value`  
 Requis. Valeur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], généralement un objet ou un tableau, à convertir.  
  
 `replacer`  
 Facultatif. Fonction ou tableau qui transforme les résultats.  
  
 Si `replacer` est une fonction, `JSON.stringify` appelle la fonction et passe la clé et la valeur de chaque membre. La valeur de retour est utilisée au lieu de la valeur d'origine. Si la fonction retourne `undefined`, le membre est exclu. La clé de l'objet racine est une chaîne vide : "".  
  
 Si `replacer` est un tableau, seuls les membres avec des valeurs de clé figurant dans le tableau sont convertis. L'ordre dans lequel les membres sont convertis est identique à celui des clés dans le tableau. Le tableau `replacer` est ignoré lorsque l'argument `value` est également un tableau.  
  
 `space`  
 Facultatif. Ajoute les caractères de mise en retrait, d'espace blanc et de saut de ligne au texte JSON de la valeur de retour pour faciliter la lecture.  
  
 Si `space` est omis, le texte de la valeur de retour est généré sans espace blanc supplémentaire.  
  
 Si `space` est un nombre, le texte de la valeur de retour est mis en retrait en respectant le nombre spécifié d'espaces blancs à chaque niveau. Si `space` est supérieur à 10, le texte est mis en retrait de 10 espaces.  
  
 Si `space` est une chaîne non vide, telle que « \t », le texte de la valeur de retour est mis en retrait avec les caractères de la chaîne à chaque niveau.  
  
 Si `space` est une chaîne d'une longueur supérieure à 10 caractères, les 10 premiers caractères sont utilisés.  
  
## <a name="return-value"></a>Valeur de retour  
 Chaîne qui contient le texte JSON.  
  
## <a name="exceptions"></a>Exceptions  
  
|Exception|Condition|  
|---------------|---------------|  
|[Argument de remplacement incorrect](../../javascript/misc/invalid-replacer-argument.md)|L'argument `replacer` n'est pas une fonction ou un tableau.|  
|[Référence circulaire dans l'argument de valeur non prise en charge](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|L'argument `value` contient une référence circulaire.|  
  
## <a name="remarks"></a>Remarques  
 Si `value` a une méthode `toJSON`, la fonction `JSON.stringify` utilise la valeur de retour de cette méthode. Si la valeur de retour de la méthode `toJSON` est `undefined`, le membre n'est pas converti. Cela permet à un objet de déterminer sa propre représentation JSON.  
  
 Les valeurs qui n'ont pas de représentations JSON, notamment `undefined`, ne sont pas converties. Dans les objets, elles sont supprimées. Dans les tableaux, elles sont remplacées par Null.  
  
 Les valeurs de chaîne commencent et se terminent par un guillemet. Tous les caractères Unicode peuvent être placés entre guillemets, à l'exception des caractères qui doivent être placés dans une séquence d'échappement à l'aide d'une barre oblique inverse. Les caractères suivants doivent être précédés d'une barre oblique inverse :  
  
-   Guillemet (")  
  
-   Barre oblique inverse (\\)  
  
-   Retour arrière (b)  
  
-   Saut de page (f)  
  
-   Saut de ligne (n)  
  
-   Retour chariot (r)  
  
-   Tabulation horizontale (t)  
  
-   Valeurs à quatre chiffres hexadécimaux (uhhhh)  
  
## <a name="order-of-execution"></a>Ordre d'exécution  
 Pendant le processus de sérialisation, si une méthode `toJSON` existe pour l'argument `value`, `JSON.stringify` appelle tout d'abord la méthode `toJSON`. Si elle n'existe pas, la valeur d'origine est utilisée. Ensuite, si un argument `replacer` est fourni, la valeur (valeur d'origine ou valeur de retour `toJSON`) est remplacée par la valeur de retour de l'argument `replacer`. Enfin, des espaces blancs sont ajoutés à la valeur en fonction de l'argument facultatif `space` pour générer le texte JSON final.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise `JSON.stringify` pour convertir l'objet `contact` en texte JSON. Le tableau `memberfilter` est défini de sorte que seuls les membres `surname` et `phone` soient convertis. Le membre `firstname` est omis.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Array();  
memberfilter[0] = "surname";  
memberfilter[1] = "phone";  
var jsonText = JSON.stringify(contact, memberfilter, "\t");  
document.write(jsonText);  
// Output:   
// { "surname": "Aaberg", "phone": [ "555-0100", "555-0120" ] }  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise `JSON.stringify` avec un tableau. La fonction `replaceToUpper` convertit chaque chaîne du tableau en majuscules.  
  
```JavaScript  
var continents = new Array();  
continents[0] = "Europe";  
continents[1] = "Asia";  
continents[2] = "Australia";  
continents[3] = "Antarctica";  
continents[4] = "North America";  
continents[5] = "South America";  
continents[6] = "Africa";  
  
var jsonText = JSON.stringify(continents, replaceToUpper);  
  
function replaceToUpper(key, value) {  
    return value.toString().toUpperCase();  
}  
  
//Output:  
// "EUROPE,ASIA,AUSTRALIA,ANTARCTICA,NORTH AMERICA,SOUTH AMERICA,AFRICA"  
  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise la méthode `toJSON` pour convertir des valeurs de chaîne en majuscules.  
  
```JavaScript  
var contact = new Object();   
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
document.write(jsonText);  
  
// Output:  
{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}  
  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [toJSON, méthode (Date)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Exemple d’application (Windows Store) de lecteur de flux](http://code.msdn.microsoft.com/Feed-reader-sample-99d68cf8)
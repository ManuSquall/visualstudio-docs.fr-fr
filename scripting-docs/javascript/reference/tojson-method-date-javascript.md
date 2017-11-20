---
title: "toJSON, méthode (Date) (JavaScript) | Documents Microsoft"
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
helpviewer_keywords: toJSON method
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a131c7b248ca0486ab0b3b02d40e4351136c37c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="tojson-method-date-javascript"></a>toJSON, méthode (Date) (JavaScript)
Utilisé par le [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) méthode pour permettre la transformation des données d’un objet pour la sérialisation de JavaScript Objet Notation (JSON).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
objectname.toJSON()  
```  
  
## <a name="parameters"></a>Paramètres  
 `objectname`  
 Obligatoire. Un objet pour le JSON sérialisation est demandée.  
  
## <a name="remarks"></a>Remarques  
 Le `toJSON` méthode est utilisée par le `JSON.stringify` (fonction). `JSON.stringify`Sérialise un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valeur en texte JSON. Si un `toJSON` méthode est fournie pour `JSON.stringify`, le `toJSON` méthode est appelée lorsque `JSON.stringify` est appelée.  
  
 Le `toJSON` méthode est un membre intégré de la [Date](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objet. Il retourne une chaîne de date au format ISO pour le fuseau horaire UTC (indiqué par le suffixe Z).  
  
 Vous pouvez remplacer le `toJSON` méthode pour le `Date` de type, ou définir un `toJSON` méthode pour d’autres types d’objet obtenir la transformation de données pour le type d’objet spécifique avant la sérialisation JSON.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `toJSON` méthode pour sérialiser les valeurs de membre de chaîne en majuscules. Le `toJSON` méthode est appelée lorsque `JSON.stringify` est appelée.  
  
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
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `toJSON` méthode est un membre intégré de la [Date](../../javascript/reference/date-object-javascript.md) objet.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]**S’applique à :** [objet de Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet JSON](../../javascript/reference/json-object-javascript.md)   
 [Fonction JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Fonction JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [Méthodes JavaScript](../../javascript/reference/javascript-methods.md)
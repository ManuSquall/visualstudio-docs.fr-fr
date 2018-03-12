---
title: "toLocaleString, méthode (Object) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- toLocaleString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleString method
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f88e1c702cd8a7d702630ae90ef840c4af88f30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-method-object-javascript"></a>toLocaleString, méthode (Object) (JavaScript)
Retourne une date convertie en une chaîne en utilisant les paramètres régionaux actuels.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.toLocaleString()   
```  
  
## <a name="remarks"></a>Remarques  
 Requis `dateObj` toute `Date` objet.  
  
 Le `toLocaleString` méthode retourne un `String` objet qui contient la date écrite sous forme de long par défaut de paramètres régionaux actuels.  
  
-   Pour les dates entre 1601 et 1999 J.-C., la date est mise en forme en fonction des paramètres régionaux du Panneau de configuration de contrôle de l’utilisateur.  
  
-   Pour les dates en dehors de cette plage, le format par défaut de la **toString** méthode est utilisée.  
  
 Par exemple, aux États-Unis, `toLocaleString` retourne « 01/05/96 00:00:00 » pour le 5 janvier. En Europe, elle retourne « 01/05/96 00:00:00 » pour la même date, comme la convention européenne place le jour précédant le mois.  
  
> [!NOTE]
>  `toLocaleString`doit uniquement être utilisé pour afficher les résultats à l’utilisateur ; Il doit jamais être utilisé comme base pour le calcul d’un script comme le résultat retourné est spécifiques à l’ordinateur.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `toLocaleString`.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [Array, objet](../../javascript/reference/array-object-javascript.md)&#124; [Date objet](../../javascript/reference/date-object-javascript.md)&#124; [Numéro d’objet](../../javascript/reference/number-object-javascript.md)&#124; [Object, objet](../../javascript/reference/object-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)
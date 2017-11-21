---
title: "ToString, méthode (Object) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ToString method
ms.assetid: c4ae9da2-60c9-486f-b00a-9df03fda4a35
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518f988486bb527220884052768e61d099dbd716
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-object-javascript"></a>toString, méthode (Object) (JavaScript)
Retourne la représentation d'un objet sous forme de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
objectname.toString([radix])  
```  
  
## <a name="parameters"></a>Paramètres  
 `objectname`  
 Obligatoire. Objet pour lequel une représentation de chaîne est recherchée.  
  
 `radix`  
 Facultatif. Spécifie une racine pour la conversion de valeurs numériques en chaînes. Cette valeur est utilisée uniquement pour les nombres.  
  
## <a name="remarks"></a>Remarques  
 Le **toString** méthode est un membre de tout intégré [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objets. Son comportement dépend du type d’objet :  
  
|Objet|Comportement|  
|------------|--------------|  
|Tableau|Éléments d’un `Array` sont convertis en chaînes. Les chaînes résultantes sont concaténées, séparées par des virgules.|  
|Booléen|Si la valeur booléenne est **true**, retourne «`true`». Sinon, retourne «`false`».|  
|Date|Retourne la représentation textuelle de la date.|  
|Erreur|Retourne une chaîne contenant le message d’erreur associé.|  
|Fonction|Retourne une chaîne sous la forme suivante, où *functionname* est le nom de la fonction dont **toString** méthode a été appelée :<br /><br /> `function functionname( ) { [native code] }`|  
|Nombre|Retourne la représentation textuelle du nombre.|  
|Chaîne|Retourne la valeur de la `String` objet.|  
|Par défaut|Retourne `"[object objectname]"`, où `objectname` est le nom du type d’objet.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **toString** méthode avec un argument radix. La valeur de retour de fonction ci-dessous est une table de conversion de base.  
  
```JavaScript  
function CreateRadixTable (){  
   var s = "";  
  
   // Create table heading.  
   s += "Hex  Dec  Bin \n";  
  
   for (x = 0; x < 16; x++)  
   {  
      s += "   ";  
  
      // Convert to hexidecimal.  
      s += x.toString(16);  
      s += "     ";  
      if (x < 10) s += "  ";  
  
      // Convert to decimal.  
      s += x.toString(10);  
      s += "     ";  
  
      // Convert to binary.  
      s += x.toString(2);  
      s += "\n";  
   }  
  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **S’applique aux**: [Array, objet](../../javascript/reference/array-object-javascript.md)&#124; [Objet Boolean](../../javascript/reference/boolean-object-javascript.md)&#124; [Date objet](../../javascript/reference/date-object-javascript.md)&#124; [Objet error](../../javascript/reference/error-object-javascript.md)&#124; [Objet de fonction](../../javascript/reference/function-object-javascript.md)&#124; [Numéro d’objet](../../javascript/reference/number-object-javascript.md)&#124; [Object, objet](../../javascript/reference/object-object-javascript.md)&#124; [Objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction function](../../javascript/reference/function-statement-javascript.md)
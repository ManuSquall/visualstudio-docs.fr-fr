---
title: "lastIndexOf, méthode (String) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: lastIndexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndexOf method, string
- string, lastIndexOf method
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fa0f35e970435a4d0296493c20afdeaac128cae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-string-javascript"></a>lastIndexOf, méthode (String) (JavaScript)
Retourne la dernière occurrence d’une sous-chaîne dans la chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## <a name="parameters"></a>Paramètres  
 `strObj`  
 Obligatoire. Objet `String` ou littéral de chaîne.  
  
 `substring`  
 Obligatoire. Sous-chaîne à rechercher.  
  
 `startindex`  
 Facultatif. Index auquel commencer la recherche. Si omis, la recherche commence à la fin de la chaîne.  
  
## <a name="remarks"></a>Remarques  
 Le **lastIndexOf** méthode retourne une valeur entière indiquant le début de la sous-chaîne dans la `String` objet. Si la sous-chaîne est introuvable, une valeur -1 est retournée.  
  
 Si `startindex` est négatif, `startindex` est considéré comme égal à 0 (zéro). Si elle est supérieure à l’index de position de caractère plus grand, il est traité comme le plus grand index possible.  
  
 La recherche est effectuée à partir du dernier caractère de la chaîne. Sinon, cette méthode est identique à **indexOf**.  
  
 L’exemple suivant illustre l’utilisation de la **lastIndexOf** (méthode).  
  
```JavaScript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode indexOf (chaîne)](../../javascript/reference/indexof-method-string-javascript.md)
---
title: Search, méthode (String) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- search
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- search method
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730fb1604147b56fc5ab1e312bf7a6dfb5487a5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639729"
---
# <a name="search-method-string-javascript"></a>search, méthode (String) (JavaScript)
Recherche la première correspondance de sous-chaîne dans une recherche d’expression régulière.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
stringObj.search(rgExp)   
```  
  
## <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Le `String` objet ou un littéral de chaîne sur laquelle effectuer la recherche.  
  
 `rgExp`  
 Obligatoire. Une instance d’un **Expression régulière** objet qui contient le modèle d’expression régulière et les indicateurs applicables.  
  
## <a name="return-value"></a>Valeur de retour  
 Si une correspondance est trouvée, le **recherche** méthode retourne un entier qui indique le décalage à partir du début de la chaîne où la première correspondance s’est produite. Si aucune correspondance n’est trouvée, elle retourne -1.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez également définir le `i` indicateur qui provoque la recherche comme respectant la casse.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **recherche** (méthode).  
  
```JavaScript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [EXEC, méthode (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match, méthode (String)](../../javascript/reference/match-method-string-javascript.md)   
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Replace, méthode (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [test, méthode (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmation d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)
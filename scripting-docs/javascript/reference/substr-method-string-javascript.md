---
title: SUBSTR, méthode (String) (JavaScript) | Documents Microsoft
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
- substr
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substr method
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b002bfefbeb81c534c882fa4a4720c93ccca185
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640029"
---
# <a name="substr-method-string-javascript"></a>substr, méthode (String) (JavaScript)
Obtient une sous-chaîne commençant à l’emplacement spécifié et dont la longueur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## <a name="parameters"></a>Paramètres  
 `stringvar`  
 Obligatoire. Un littéral de chaîne ou `String` à partir de laquelle la sous-chaîne est extraite de l’objet.  
  
 `start`  
 Obligatoire. Position de départ de la sous-chaîne souhaitée. L’index du premier caractère dans la chaîne est égale à zéro.  
  
 `length`  
 Facultatif. Le nombre de caractères à inclure dans la sous-chaîne retournée.  
  
## <a name="remarks"></a>Remarques  
 Si `length` est égal à zéro ou négative, une chaîne vide est retournée. Si non spécifié, la sous-chaîne continue jusqu'à la fin de `stringvar`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `substr`.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode substring (String)](../../javascript/reference/substring-method-string-javascript.md)
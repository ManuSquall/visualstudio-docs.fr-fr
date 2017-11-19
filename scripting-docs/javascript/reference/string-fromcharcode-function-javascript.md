---
title: String.fromCharCode, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: fromCharCode
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- fromCharCodeAt method
- characters, from Unicode
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbcd9062d7da0b73647c1d9eb6cc207af23c3532
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="stringfromcharcode-function-javascript"></a>String.fromCharCode, fonction (JavaScript)
Retourne une chaîne à partir d'un certain nombre de valeurs de caractères Unicode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## <a name="parameters"></a>Paramètres  
 `String`  
 Obligatoire. Objet `String`.  
  
 `code1`, . . . , `codeN`  
 Facultatif. Une série de valeurs de caractères Unicode à convertir en une chaîne. Si aucun argument n’est fourni, le résultat est une chaîne vide.  
  
## <a name="remarks"></a>Remarques  
 Vous appelez cette fonction sur le `String` objet plutôt que sur une instance de chaîne.  
  
 L’exemple suivant montre comment utiliser cette méthode :  
  
```JavaScript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode charCodeAt (String)](../../javascript/reference/charcodeat-method-string-javascript.md)
---
title: concat, méthode (String) (JavaScript) | Documents Microsoft
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
- concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (String)
- Concat method
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b6419cc6404e06fc780802a30a3b4add8320881
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633999"
---
# <a name="concat-method-string-javascript"></a>concat, méthode (String) (JavaScript)
Retourne une chaîne qui contient la concaténation de deux ou plusieurs chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## <a name="parameters"></a>Paramètres  
 `string1`  
 Obligatoire. Le `String` objet ou un littéral de chaîne à laquelle toutes les autres spécifié de chaînes sont concaténées.  
  
 `string2,. . ., stringN`  
 Facultatif. Les chaînes à ajouter à la fin de `string1`.  
  
## <a name="remarks"></a>Remarques  
 Le résultat de la `concat` méthode équivaut à : `result`  =  `string1`  +  `string2`  +  `string3`  +  `stringN`. Une modification de valeur de chaîne d’une source ou le résultat n’affecte pas la valeur dans l’autre chaîne. Si un des arguments ne sont pas des chaînes, ils sont tout d’abord convertis en chaînes avant d’être concaténé à `string1`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `concat` méthode avec une chaîne :  
  
```JavaScript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur d'addition (+)](../../javascript/reference/addition-operator-decrement-javascript.md)
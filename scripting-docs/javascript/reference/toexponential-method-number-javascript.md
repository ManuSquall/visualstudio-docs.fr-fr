---
title: toExponential, méthode (Number) (JavaScript) | Documents Microsoft
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
- toExponential
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toExponential method
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fff2f2bc0c443fa9308c8d01dcea42a3cec9ff04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640289"
---
# <a name="toexponential-method-number-javascript"></a>toExponential, méthode (Number) (JavaScript)
Représente un nombre en notation exponentielle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## <a name="parameters"></a>Paramètres  
 `numObj`  
 Obligatoire. A **nombre** objet.  
  
 `fractionDigits`  
 Facultatif. Le nombre de chiffres après la virgule décimale. Doit être dans la plage 0 - 20, inclus.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une représentation sous forme de chaîne d’un nombre en notation exponentielle. La chaîne comporte un chiffre avant la virgule décimale et peut contenir `fractionDigits` chiffres après lui.  
  
 Si `fractionDigits` n’est pas fourni, le `toExponential` méthode retourne autant de chiffres nécessaire de spécifier le nombre de façon unique.  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique aux**: [numéro d’objet](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [toFixed, méthode (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Méthode toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)
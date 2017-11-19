---
title: "toPrecision, méthode (Number) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toPrecision
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toPrecision method
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeab7642dcd88677d1b5a7102e3cf342d7ee1d29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="toprecision-method-number-javascript"></a>toPrecision, méthode (Number) (JavaScript)
Représente un nombre en notation exponentielle ou à virgule fixe avec un nombre spécifié de chiffres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## <a name="parameters"></a>Paramètres  
 `numObj`  
 Obligatoire. Objet `Number`.  
  
 `precision`  
 Facultatif. Le nombre de chiffres significatifs. Doit être dans la plage 1-21, inclus.  
  
## <a name="return-value"></a>Valeur de retour  
 Pour les nombres en notation exponentielle, `precision` - 1 chiffres sont retournés après la virgule décimale. Pour les nombres à virgule fixe, `precision` chiffres significatifs sont retournés.  
  
 Si `precision` n’est pas fourni ou est **non défini**, le **toString** méthode est appelée à la place.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser `toPrecision`.  
  
```JavaScript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique aux**: [numéro d’objet](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [toFixed, méthode (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Méthode toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)
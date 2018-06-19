---
title: toFixed, méthode (Number) (JavaScript) | Documents Microsoft
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
- toFixed
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toFixed method
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51dd67632f4e6417fee72fd19575025423bbf1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640399"
---
# <a name="tofixed-method-number-javascript"></a>toFixed, méthode (Number) (JavaScript)
Représente un nombre à virgule fixe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## <a name="parameters"></a>Paramètres  
 `numObj`  
 Requis A `Number` objet.  
  
 `fractionDigits`  
 Facultatif. Le nombre de chiffres après la virgule décimale. Doit être dans la plage 0 - 20, inclus.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une représentation sous forme de chaîne d’un nombre à virgule fixe, contenant `fractionDigits` chiffres après la virgule décimale.  
  
 Si `fractionDigits` n’est pas fourni ou **non défini**, la valeur par défaut est égale à zéro.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser `toFixed`.  
  
```JavaScript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique aux**: [numéro d’objet](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [toExponential, méthode (Number)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [Méthode toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)
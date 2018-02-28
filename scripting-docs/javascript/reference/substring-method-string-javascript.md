---
title: "SUBSTRING, méthode (String) (JavaScript) | Documents Microsoft"
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
- substring
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substrings
- substring method
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15ebaadc7b24fa97f531a22f6deb1453ff52b3e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="substring-method-string-javascript"></a>substring, méthode (String) (JavaScript)
Retourne la sous-chaîne à l’emplacement spécifié dans un `String` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## <a name="parameters"></a>Paramètres  
 `start`  
 Obligatoire. Entier de l’index de base zéro indiquant le début de la sous-chaîne.  
  
 `end`  
 Facultatif. Entier de l’index de base zéro qui indique la fin de la sous-chaîne. La sous-chaîne inclut tous les caractères jusqu'à, mais non compris le caractère indiqué par `end`.  
  
 Si `end` est omis, les caractères de `start` jusqu'à la fin de la chaîne d’origine sont retournés.  
  
## <a name="remarks"></a>Remarques  
 Le `substring` méthode retourne une chaîne contenant la sous-chaîne à partir de `start` jusqu'à, mais non compris, `end`.  
  
 Le **sous-chaîne** méthode utilise la valeur inférieure de `start` et `end` comme point de début de la sous-chaîne. Par exemple, strvar.substring (0, 3**)** et strvar.substring (3, 0) retournent la même sous-chaîne.  
  
 Si le paramètre `start` ou `end` est `NaN` ou négative, elle est remplacée par zéro.  
  
 La longueur de la sous-chaîne est égale à la valeur absolue de la différence entre `start` et `end`. Par exemple, la longueur de la sous-chaîne retournée dans strvar.substring (0, 3) et strvar.substring (3, 0) est de trois.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **sous-chaîne** (méthode).  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode substr (String)](../../javascript/reference/substr-method-string-javascript.md)
---
title: with, instruction (JavaScript) | Documents Microsoft
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
- with_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- With statement
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d49b13261c66cde0ecd53517a99361f6aecb79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="with-statement-javascript"></a>with, instruction (JavaScript)
Définit l'objet par défaut d'une instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
with (object) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Paramètres  
 `object`  
 Objet par défaut.  
  
 `statements`  
 Une ou plusieurs instructions pour lesquelles `object` est l'objet par défaut.  
  
## <a name="remarks"></a>Remarques  
 L'instruction `with` est généralement utilisée pour diminuer la quantité de code à écrire dans certaines situations.  
  
> [!WARNING]
>  L'utilisation de `with` n'est pas autorisée en mode strict. L'utilisation de `with` peut rendre le code plus difficile à lire et à déboguer et doit généralement être évitée.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, l'objet `Math` est utilisé de façon répétée :  
  
```JavaScript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## <a name="example"></a>Exemple  
 Si vous réécrivez l'exemple pour utiliser l'instruction `with`, votre code devient plus succinct :  
  
```JavaScript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction this](../../javascript/reference/this-statement-javascript.md)
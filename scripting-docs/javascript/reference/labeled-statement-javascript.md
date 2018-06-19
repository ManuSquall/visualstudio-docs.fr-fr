---
title: Une instruction (JavaScript) étiquetée | Documents Microsoft
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
- labeled_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- continue statement
- labeled statement
- identifiers, statements
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd72b15d3fc9083ca127a48981c0cd0a7ee56b6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637599"
---
# <a name="labeled-statement-javascript"></a>Labeled, instruction (JavaScript)
Fournit un identificateur pour une instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      label :  
   statements   
```  
  
## <a name="parameters"></a>Paramètres  
 *étiquette*  
 Obligatoire. Identificateur unique utilisé pour faire référence à l’instruction étiquetée.  
  
 `statements`  
 Facultatif. Une ou plusieurs instructions associées *étiquette*.  
  
## <a name="remarks"></a>Remarques  
 Les étiquettes sont utilisées par le **saut** et **continuer** instructions afin de spécifier l’instruction à laquelle le **saut** et **continuer** s’appliquent.  
  
## <a name="example"></a>Exemple  
 Dans le code suivant, le **continuer** instruction fait référence à la **pour** boucle est précédé par le `Inner:` instruction. Lorsque `j` est 24, la **continuer** qui provoque l’instruction **pour** boucle à passer à l’itération suivante. Les nombres 21 à 23 et 25 à 30 impriment sur chaque ligne.  
  
```JavaScript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [Instruction continue](../../javascript/reference/continue-statement-javascript.md)
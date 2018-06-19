---
title: index, propriété (RegExp) (JavaScript) | Documents Microsoft
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
- index
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Index property
- matching strings
ms.assetid: d8be1ef6-1bf2-43cd-b0b5-567a61eabaad
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c6b11a5caf6e727b4d525b9a2d51eddd4542bc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637359"
---
# <a name="index-property-regexp-javascript"></a>index, propriété (RegExp) (JavaScript)
Retourne la position de caractère où commence à la première correspondance dans une chaîne recherchée. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RegExp.index   
```  
  
## <a name="remarks"></a>Remarques  
 L’objet associé à cette propriété est toujours global `RegExp` objet.  
  
 Le **index** propriété est de base zéro. La valeur initiale de la **index** propriété est -1. Sa valeur change chaque fois qu’une correspondance réussie est établie.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **index** propriété. Cette fonction effectue une itération d’une chaîne de recherche et imprime la **index** et `lastIndex` valeurs pour chaque mot dans la chaîne.  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)
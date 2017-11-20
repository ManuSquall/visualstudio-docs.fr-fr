---
title: "lastIndex, propriété (RegExp) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: lastIndex
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: lastIndex property
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5e24fe14d335e1494b13518543f56025625de0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="lastindex-property-regexp-javascript"></a>lastIndex, propriété (RegExp) (JavaScript)
Retourne la position de caractère où la correspondance suivante commence dans une chaîne recherchée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RegExp.lastIndex  
```  
  
## <a name="remarks"></a>Remarques  
 L’objet associé à cette propriété est toujours global `RegExp` objet.  
  
 Le `lastIndex` propriété zéro, c'est-à-dire que l’index du premier caractère est égal à zéro. Sa valeur initiale est -1. Sa valeur est modifiée chaque fois qu’une correspondance réussie est établie.  
  
 Le `lastIndex` propriété est modifiée par le `exec` et **test** méthodes de la `RegExp` objet et le `match`, **remplacer**, et **fractionner**méthodes de la `String` objet.  
  
 Les règles suivantes s’appliquent aux valeurs de `lastIndex`:  
  
-   Si aucune correspondance, `lastIndex` a la valeur -1.  
  
-   Si `lastIndex` est supérieur à la longueur de la chaîne, **test** et `exec` échouer et `lastIndex` a la valeur -1.  
  
-   Si `lastIndex` est égal à la longueur de la chaîne, l’expression régulière correspond si le modèle correspond à une chaîne vide. Dans le cas contraire, la correspondance échoue et `lastIndex` est réinitialisé à -1.  
  
-   Sinon, `lastIndex` est définie sur la première position qui suit la correspondance la plus récente.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `lastIndex` propriété. Cette fonction effectue une itération d’une chaîne de recherche et imprime la **index** et `lastIndex` valeurs pour chaque mot dans la chaîne.  
  
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
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)
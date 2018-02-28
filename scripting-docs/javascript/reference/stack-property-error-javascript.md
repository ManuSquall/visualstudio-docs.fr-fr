---
title: "Stack, propriété (Error) (JavaScript) | Documents Microsoft"
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
- Error.stack
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript error stack
- error stack [JavaScript]
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e4a2537b1543b7e8d9727afdeb8ea5dee61bbc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="stack-property-error-javascript"></a>stack, propriété (Error) (JavaScript)
Obtient ou définit la pile d'erreur sous forme de chaîne qui contient les images de frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.stack   
```  
  
## <a name="remarks"></a>Remarques  
 La propriété `stack` prend la valeur `undefined` quand l'erreur est construite et obtient les informations de trace quand l'erreur est levée. Si une erreur se produit plusieurs fois, la propriété `stack` est mise à jour chaque fois que l'erreur est levée.  
  
 Frames de pile sont affichés dans le format suivant : **à nomfonction (\</URL de nom qualifié complet > :\<numéro de ligne > :\<numéro de colonne >)**  
  
 Si vous créez votre propre objet d'erreur et que vous affectez une valeur au frame de pile, la valeur n'est pas remplacée quand l'erreur est levée.  
  
 La propriété `stack` n'affiche pas les fonctions inline dans ses frames. Elle affiche uniquement la pile physique.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment obtenir la pile quand vous interceptez une erreur.  
  
```JavaScript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment définir puis obtenir la pile.  
  
```JavaScript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **S’applique aux**: [objet Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, propriété (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [message, propriété (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Name, propriété (Error)](../../javascript/reference/name-property-error-javascript.md)   
 [Propriété stackTraceLimit (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)
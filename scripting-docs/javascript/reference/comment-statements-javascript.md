---
title: "Commentaire d’instructions (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Comment_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comments, ignoring
- comment statements
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c270379725550e116928bbecd69e6be51c34992f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="comment-statements-javascript"></a>Comment, instructions (JavaScript)
Empêche la prise en compte des commentaires par l'analyseur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## <a name="remarks"></a>Remarques  
 L'argument `comment` représente le texte des commentaires que vous souhaitez inclure dans votre script. L'argument `condStatement` est utilisé en cas d'activation de la compilation conditionnelle. Lors de l'utilisation de commentaires sur une seule ligne, les caractères « // » et « @ » peuvent ne pas être séparés par un espace.  
  
 Utilisez les commentaires pour éviter la lecture de certaines parties d'un script par l'analyseur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Utilisez les commentaires pour inclure des notes explicatives dans un programme.  
  
 Dans le cas de l'utilisation de commentaires sur une seule ligne, l'analyseur ignore le texte compris entre le marqueur de commentaire et la fin de la ligne. Dans le cas de l'utilisation de commentaires sur plusieurs lignes, l'analyseur ignore le texte compris entre les marqueurs de début et les marqueurs de fin.  
  
 Les commentaires permettent de prendre en charge la compilation conditionnelle tout en restant compatibles avec des navigateurs qui ne prennent pas en charge cette fonctionnalité. Ces navigateurs traitent ces formes de commentaires respectivement comme des commentaires sur une seule ligne ou des commentaires sur plusieurs lignes.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre les principales utilisations des commentaires.  
  
```JavaScript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser la compilation conditionnelle. Cet exemple utilise des délimiteurs de commentaires spéciaux qui sont utilisés uniquement si la compilation conditionnelle est activée par l'instruction `@cc_on`. Les moteurs de script qui ne prennent pas en charge la compilation conditionnelle traitent uniquement le message relatif à cette non prise en charge.  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]
---
title: "Trim, méthode (String) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- trim method
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de358981cfbf569ef35be95b55b3e9856027df35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="trim-method-string-javascript"></a>trim, méthode (String) (JavaScript)
Supprime les espaces blancs de début et de fin ainsi que les marques de fin de ligne d'une chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
stringObj.trim()  
```  
  
## <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Objet `String` ou littéral de chaîne. Cette chaîne n'est pas modifiée par la méthode `trim`.  
  
## <a name="return-value"></a>Valeur de retour  
 Chaîne d'origine dans laquelle les espaces blancs de début et de fin et les caractères de fin de ligne sont supprimés.  
  
## <a name="remarks"></a>Remarques  
 Les caractères supprimés comprennent l'espace, la tabulation, le saut de page, le retour chariot et le saut de ligne. Consultez [des caractères spéciaux](../../javascript/advanced/special-characters-javascript.md) pour une liste complète des espaces blancs et la ligne de caractères de marque de fin.  
  
 Pour obtenir un exemple qui montre comment implémenter votre propre méthode trim, consultez [Prototypes et héritage de Prototype](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `trim`.  
  
```JavaScript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Caractères spéciaux](../../javascript/advanced/special-characters-javascript.md)   
 [Objet String](../../javascript/reference/string-object-javascript.md)   
 [Exemple d’application de défilement, panoramique et zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)
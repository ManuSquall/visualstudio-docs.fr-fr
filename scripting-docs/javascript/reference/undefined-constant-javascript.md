---
title: "non défini (constante) (JavaScript) | Documents Microsoft"
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
- undefined
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- undefined property
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ba7fa8b160e4f5d954c8d6545da5fae41c2f74b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="undefined-constant-javascript"></a>Constante non définie (JavaScript)
Une valeur qui a jamais été définie, telle qu’une variable qui n’a pas été initialisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
undefined  
```  
  
## <a name="remarks"></a>Remarques  
 Le `undefined` constant est un membre de la `Global` de l’objet et devient disponible lorsque le moteur de script est initialisé. Lorsqu’une variable a été déclarée, mais ne pas initialisée, sa valeur est **non défini**.  
  
 Si une variable n’a pas été déclarée, vous ne pouvez pas le comparer à `undefined`, mais vous pouvez comparer le type de la variable à la chaîne « non définie ».  
  
 Le `undefined` constante est utile lorsque explicitement test ou en définissant une variable pour non défini.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `undefined` constante.  
  
```JavaScript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## <a name="requirements"></a>Spécifications  
 Le `undefined` propriété a été introduite dans [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)]et a été effectuée en lecture seule dans [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)].  
  
 **S’applique aux**: [objet Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)
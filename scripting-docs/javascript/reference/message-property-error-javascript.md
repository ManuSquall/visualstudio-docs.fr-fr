---
title: "message, propriété (Error) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: message
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Message property
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dbd2db6c6d31dc48d90c3b07d2388eacf73ae7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="message-property-error-javascript"></a>message, propriété (Error) (JavaScript)
Retourne une chaîne de message d’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
errorObj.message  
```  
  
## <a name="parameters"></a>Paramètres  
 `errorObj`  
 Obligatoire. Instance de `Error` objet.  
  
## <a name="remarks"></a>Remarques  
 Le `message` propriété retourne une chaîne qui contient un message d’erreur associé à une erreur spécifique.  
  
 Le `description` et `message` propriétés fournissent les mêmes fonctionnalités. Le `description` propriété fournit une compatibilité descendante ; le `message` propriété respecte la norme ECMA.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant provoque la levée d’une exception TypeError et affiche le nom de l’erreur et son message.  
  
```JavaScript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>Exemple  
 La sortie de ce code est comme suit.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **S’applique aux**: [objet Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, propriété (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Propriété name (Error)](../../javascript/reference/name-property-error-javascript.md)
---
title: Description, propriété (Error) (JavaScript) | Documents Microsoft
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
- Description
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, error description
- Description property
- errors, description
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6135951fdf65698ed48b9bbacdcc55c1aac22d41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636359"
---
# <a name="description-property-error-javascript"></a>description, propriété (Error) (JavaScript)
Retourne ou définit la chaîne descriptive associée à une erreur spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## <a name="parameters"></a>Paramètres  
 *object*  
 Obligatoire. N’importe quelle instance d’un `Error` objet.  
  
 `stringExpression`  
 Facultatif. Une expression de chaîne qui contient une description de l’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le **description** propriété contient la chaîne de message d’erreur associée à une erreur spécifique. La valeur contenue dans cette propriété permet d’informer l’utilisateur d’une erreur.  
  
 Le **description** et **message** propriétés fournissent les mêmes fonctionnalités ; le **description** propriété offre une compatibilité descendante ; le  **message** propriété respecte la norme ECMA.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **description** propriété.  
  
```JavaScript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **S’applique aux**: [objet Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Number, propriété (Error)](../../javascript/reference/number-property-error-javascript.md)   
 [message, propriété (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Propriété name (Error)](../../javascript/reference/name-property-error-javascript.md)
---
title: Number, propriété (Error) (JavaScript) | Documents Microsoft
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
- Number
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number property
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbc229e7d0572e1a3dbed056b344da7ff9ce7292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639099"
---
# <a name="number-property-error-javascript"></a>number, propriété (Error) (JavaScript)
Retourne ou définit la valeur numérique associée à une erreur spécifique. Le `Error` propriété par défaut de l’objet est **nombre**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## <a name="parameters"></a>Paramètres  
 *Objet*  
 N’importe quelle instance de la `Error` objet.  
  
 *errorNumber*  
 Entier qui représente une erreur.  
  
## <a name="remarks"></a>Remarques  
 Un numéro d'erreur est une valeur 32 bits. Le mot de 16 bits supérieur est le code de fonction, et le mot de poids faible est le code d’erreur. Pour déterminer le code d’erreur, utilisez le `&` (au niveau du bit et) opérateur à combiner la propriété number avec le nombre hexadécimal `0xFFFF`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant provoque la levée d’une exception et affiche le code d’erreur qui est dérivé du numéro d’erreur.  
  
```JavaScript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## <a name="example"></a>Exemple  
 La sortie de ce code est comme suit.  
  
```JavaScript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **S’applique aux**: [objet Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, propriété (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [message, propriété (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Propriété name (Error)](../../javascript/reference/name-property-error-javascript.md)
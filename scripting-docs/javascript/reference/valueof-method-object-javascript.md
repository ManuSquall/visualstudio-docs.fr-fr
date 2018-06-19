---
title: valueOf, méthode (Object) (JavaScript) | Documents Microsoft
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
- valueOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- valueOf method
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677b56fd6fc142ce175b130d2f83291c1ac9535f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641629"
---
# <a name="valueof-method-object-javascript"></a>valueOf, méthode (Object) (JavaScript)
Retourne la valeur primitive de l'objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.valueOf( )  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `object` référence est toute intrinsèque [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objet.  
  
 Le `valueOf` méthode définie différemment pour chaque intrinsèque [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objet.  
  
|Objet|Valeur de retour|  
|------------|------------------|  
|Tableau|Retourne l’instance de tableau.|  
|Booléen|La valeur booléenne.|  
|Date|La valeur stockée de temps en millisecondes écoulées depuis minuit, le 1er janvier 1970 UTC.|  
|Fonction|La fonction elle-même.|  
|Nombre|Valeur numérique.|  
|Objet|L’objet lui-même. Il s'agit de la valeur par défaut.|  
|Chaîne|Valeur de chaîne.|  
  
 Le **mathématiques** et `Error` objets n’ont pas un `valueOf` (méthode).  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **S’applique aux**: [Array, objet](../../javascript/reference/array-object-javascript.md)&#124; [Objet Boolean](../../javascript/reference/boolean-object-javascript.md)&#124; [Date objet](../../javascript/reference/date-object-javascript.md)&#124; [Objet de fonction](../../javascript/reference/function-object-javascript.md)&#124; [Numéro d’objet](../../javascript/reference/number-object-javascript.md)&#124; [Object, objet](../../javascript/reference/object-object-javascript.md)&#124; [Objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode toString (Object)](../../javascript/reference/tostring-method-object-javascript.md)
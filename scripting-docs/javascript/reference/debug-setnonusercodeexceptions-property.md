---
title: "Debug.setnonusercodeexceptions, propriété | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f53084d5580bc7b6b6c6356268dc60f519b2bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="debugsetnonusercodeexceptions-property"></a>Debug.setNonUserCodeExceptions, propriété
Détermine si tous les blocs try-catch dans cette portée doivent être traités par le débogueur comme non gérées par l’utilisateur. Les exceptions peuvent être classées comme levée, non gérées par l’utilisateur ou non gérées.  
  
 Si cette propriété a la valeur `true` dans l’étendue donnée, le débogueur peut déterminer à effectuer une opération (par exemple, saut) sur les exceptions levées à l’intérieur de cette étendue si le développeur souhaite s’arrêter sur les exceptions non gérées par l’utilisateur. Si cette propriété a la valeur `false` est le même que si la propriété n’a jamais été définie.  
  
 Pour plus d’informations sur le débogage, consultez [présentation de débogage de Script Active](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment définir cette propriété.  
  
```JavaScript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]
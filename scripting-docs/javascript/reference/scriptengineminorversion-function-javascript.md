---
title: ScriptEngineMinorVersion, fonction (JavaScript) | Documents Microsoft
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
- ScriptEngineMinorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMinorVersion function
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1be01c0ee10cac1c68d4750455151032a59a8e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="scriptengineminorversion-function-javascript"></a>ScriptEngineMinorVersion, fonction (JavaScript)
Obtient le numéro de version secondaire du moteur de script employé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ScriptEngineMinorVersion()  
```  
  
## <a name="remarks"></a>Remarques  
 La valeur de retour correspond directement aux informations de version contenues dans la bibliothèque de liens dynamiques (DLL) du langage de script utilisé.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la fonction `ScriptEngineMinorVersion`.  
  
```JavaScript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ScriptEngine, fonction](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion, fonction](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Fonction ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)
---
title: IActiveScriptParse32::InitNew | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 31de8258ae13855741c6dd5ca9e4ff2c589e97bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Initialise le moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur s’est produite lors de l’initialisation.  
  
## <a name="remarks"></a>Remarques  
 Avant de pouvoir utiliser le moteur de script, une des méthodes suivantes doit être appelée : `IPersist*::Load`, `IPersist*::InitNew`, ou `IActiveScriptParse32::InitNew`. La sémantique de cette méthode est identique à `IPersistStreamInit::InitNew`, dans la mesure où cette méthode indique au moteur de script pour s’initialiser. Notez qu’il n’est pas valide pour appeler à la fois `IPersist*::InitNew` ou `IActiveScriptParse32::InitNew` et `IPersist*::Load`, et n’est pas valide pour appeler `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, ou `IPersist*::Load` plusieurs fois.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)
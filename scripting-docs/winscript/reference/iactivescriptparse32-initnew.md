---
title: IActiveScriptParse32::InitNew | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 685c596caa61a5cbd5042fad3a1bfb39c349c1b1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094690"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Initialise le moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur s’est produite lors de l’initialisation.  
  
## <a name="remarks"></a>Notes  
 Avant de pouvoir utiliser le moteur de script, une des méthodes suivantes doit être appelée : `IPersist*::Load`, `IPersist*::InitNew`, ou `IActiveScriptParse32::InitNew`. La sémantique de cette méthode est identique à `IPersistStreamInit::InitNew`, car cette méthode indique au moteur de script pour s’initialiser. Notez qu’il n’est pas valide pour appeler les opérations `IPersist*::InitNew` ou `IActiveScriptParse32::InitNew` et `IPersist*::Load`, et n’est pas valide d’appeler `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, ou `IPersist*::Load` plusieurs fois.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)
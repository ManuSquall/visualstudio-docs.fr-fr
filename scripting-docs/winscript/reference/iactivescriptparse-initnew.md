---
title: IActiveScriptParse::InitNew | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55d38031708694aa777f7598f261afdfc2b4f3b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009314"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Initialise le moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur s’est produite lors de l’initialisation.  
  
## <a name="remarks"></a>Notes  
 Avant de pouvoir utiliser le moteur de script, une des méthodes suivantes doit être appelée : `IPersist*::Load`, `IPersist*::InitNew`, ou `IActiveScriptParse::InitNew`. La sémantique de cette méthode est identique à `IPersistStreamInit::InitNew`, car cette méthode indique au moteur de script pour s’initialiser. Notez qu’il n’est pas valide pour appeler les opérations `IPersist*::InitNew` ou `IActiveScriptParse::InitNew` et `IPersist*::Load`, et n’est pas valide d’appeler `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, ou `IPersist*::Load` plusieurs fois.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)
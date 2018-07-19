---
title: IActiveScriptParse::InitNew | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e34094bcc25c0316fa670f570d8b2664acc0ba78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724479"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Initialise le moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur s’est produite lors de l’initialisation.  
  
## <a name="remarks"></a>Remarques  
 Avant de pouvoir utiliser le moteur de script, une des méthodes suivantes doit être appelée : `IPersist*::Load`, `IPersist*::InitNew`, ou `IActiveScriptParse::InitNew`. La sémantique de cette méthode est identique à `IPersistStreamInit::InitNew`, dans la mesure où cette méthode indique au moteur de script pour s’initialiser. Notez qu’il n’est pas valide pour appeler à la fois `IPersist*::InitNew` ou `IActiveScriptParse::InitNew` et `IPersist*::Load`, et n’est pas valide pour appeler `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, ou `IPersist*::Load` plusieurs fois.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)
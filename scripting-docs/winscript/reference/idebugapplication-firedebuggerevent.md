---
title: 'IDebugApplication :: FireDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00d895ed484e37f0ba38636a409876156ed97287
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575007"
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Déclenche un événement générique dans l’interface `IApplicationDebugger` du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `riid`  
 dans GUID de l’objet.  
  
 `punk`  
 dans Objet d’événement à passer au débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|La méthode n’est pas implémentée actuellement.|  
  
## <a name="remarks"></a>Notes  
 La sémantique du GUID et du `IUnknown` sont entièrement définies par l’application/le débogueur.  
  
 Cette méthode permet d’obtenir des extensions personnalisées du modèle de débogueur. elle n’est pas implémentée actuellement.  
  
 Cette méthode provoque l’appel de `IApplicationDebugger::onDebuggerEvent`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)
---
title: 'IApplicationDebugger :: onDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebuggerEvent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8edb2a3c39d639b5b6722707d7b6c0b57a5c19
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577862"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Gère un événement d’application personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `riid`  
 dans Identificateur d’interface de l’objet.  
  
 `punk`  
 dans Objet d’événement qui implémente l’interface définie par `riid`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|La méthode n’est pas implémentée actuellement.|  
  
## <a name="remarks"></a>Notes  
 La sémantique de l' `IUnknown` est entièrement définie par application/débogueur.  
  
 Cette méthode permet d’obtenir des extensions personnalisées du modèle de débogueur. elle n’est pas implémentée actuellement.  
  
 Cette méthode est appelée lorsque `IDebugApplication::FireDebuggerEvent` est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)
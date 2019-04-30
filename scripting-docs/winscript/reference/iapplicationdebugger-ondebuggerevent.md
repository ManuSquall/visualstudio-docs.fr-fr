---
title: IApplicationDebugger::onDebuggerEvent | Microsoft Docs
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
ms.openlocfilehash: b78bb3345463dfd682534dc60a216f3e0e8fdf2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991361"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Gère un événement d’application personnalisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `riid`  
 [in] L’identificateur d’interface pour l’objet.  
  
 `punk`  
 [in] L’objet d’événement, qui implémente l’interface définie par `riid`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|La méthode n’est pas implémentée actuellement.|  
  
## <a name="remarks"></a>Notes  
 La sémantique de la `IUnknown` est entièrement définie par le débogueur/application.  
  
 Cette méthode permet à des extensions personnalisées du modèle débogueur ; Il n’est pas implémentée actuellement.  
  
 Cette méthode est appelée lorsque `IDebugApplication::FireDebuggerEvent` est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IApplicationDebugger (Interface)](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)
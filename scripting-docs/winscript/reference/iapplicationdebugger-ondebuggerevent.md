---
title: IApplicationDebugger::onDebuggerEvent | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebugger.onDebuggerEvent
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 754c56b8474a5e21a05c1399540391197c373118
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Gère un événement d’application personnalisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|La méthode n’est pas implémentée actuellement.|  
  
## <a name="remarks"></a>Remarques  
 La sémantique de la `IUnknown` est entièrement définie/débogueur d’application.  
  
 Cette méthode permet des extensions personnalisées du modèle débogueur ; Il n’est pas implémentée actuellement.  
  
 Cette méthode est appelée lorsque `IDebugApplication::FireDebuggerEvent` est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IApplicationDebugger (Interface)](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)
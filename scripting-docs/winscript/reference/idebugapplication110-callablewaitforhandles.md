---
title: IDebugApplication110::CallableWaitForHandles | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b259f5296f8e0b32def793a81e4c2e1069643306
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Attend qu’une des poignées spécifiées soit signalé tout en autorisant inter-threads appelle publication sur ce thread. Cette méthode doit être appelée à partir du thread de débogueur.  
  
> [!IMPORTANT]
>  [IDebugApplication110 (Interface)](../../winscript/reference/idebugapplication110-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `handleCount`  
 Le nombre de handles d’attente pour.  
  
 `pHandles`  
 Le jeu de handles d’attente pour.  
  
 `pIndex`  
 Lorsque la valeur HRESULT est S_OK, l’index dans `pHandles` pour le handle a été signalé.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)
---
title: 'IDebugApplication110 :: CallableWaitForHandles | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575087"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Attend que l’un des handles spécifiés soit signalé tout en autorisant la publication d’appels inter-threads sur ce thread. Cette méthode doit être appelée à partir du thread du débogueur.  
  
> [!IMPORTANT]
> L' [interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) est implémentée par PDM v 11.0 et ultérieur. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `handleCount`  
 Nombre de handles à attendre.  
  
 `pHandles`  
 Ensemble de handles à attendre.  
  
 `pIndex`  
 Lorsque la valeur HRESULT est S_OK, l’index dans `pHandles` pour le handle qui a été signalé.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)
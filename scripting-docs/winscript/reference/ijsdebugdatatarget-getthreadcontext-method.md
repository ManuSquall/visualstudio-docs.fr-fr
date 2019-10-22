---
title: 'IJsDebugDataTarget :: GetThreadContext, méthode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577659"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext, méthode
Récupère le contexte du thread donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadId`  
 dans Thread s’exécutant dans le processus cible.  
  
 `contextFlags`  
 dans Spécifie des indicateurs de contexte. Il est identique au champ ContextFlags du contexte (pour plus d’informations, consultez Winnt. h, recherchez CONTEXT_ALL).  
  
 `contextSize`  
 dans Taille de la mémoire tampon spécifiée par pContext.  
  
 `pContext`  
 à Reçoit une structure de contexte spécifique à la plateforme dans la mémoire tampon spécifiée par pContext.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)
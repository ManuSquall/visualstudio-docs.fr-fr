---
title: Ijsdebugdatatarget::GetThreadContext, méthode | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4e2f858c66eda2ad09b04d7beab776c793b6f195
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728179"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext, méthode
Contexte récupère pour fonction de thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadId`  
 [in] Thread en cours d’exécution dans le processus cible.  
  
 `contextFlags`  
 [in] Spécifie des indicateurs de contexte. Cela est identique à celui du champ ContextFlags du contexte (pour plus d’informations, consultez winnt.h, recherchez CONTEXT_ALL).  
  
 `contextSize`  
 [in] La taille de la mémoire tampon spécifiée par pContext.  
  
 `pContext`  
 [out] Reçoit la structure de contexte spécifiques à la plateforme dans la mémoire tampon spécifié par pContext.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)
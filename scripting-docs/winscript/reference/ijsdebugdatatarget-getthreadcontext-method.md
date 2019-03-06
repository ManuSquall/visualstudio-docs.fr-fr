---
title: Méthode IJsDebugDataTarget::GetThreadContext | Microsoft Docs
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
ms.openlocfilehash: 50e2bdb7b8720549aac5e5b3c4cebffc4b7ae892
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090061"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext, méthode
Récupère le contexte pour un thread donné.  
  
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
 [in] Thread en cours d’exécution dans le processus cible.  
  
 `contextFlags`  
 [in] Spécifie les indicateurs de contexte. Il est identique au champ ContextFlags du contexte (pour plus d’informations, consultez winnt.h, recherchez CONTEXT_ALL).  
  
 `contextSize`  
 [in] La taille de la mémoire tampon spécifiée par pContext.  
  
 `pContext`  
 [out] Reçoit la structure de contexte spécifiques à la plateforme dans la mémoire tampon spécifié par pContext.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)
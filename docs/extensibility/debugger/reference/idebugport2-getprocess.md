---
title: IDebugPort2::GetProcess | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPort2::GetPortSupplier
helpviewer_keywords: IDebugPort2::GetPortSupplier
ms.assetid: 3e2431b0-0e19-450d-8e1d-d7c314c8f872
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 229a005faf4ed349f74fbeaaa5efc464474b1e0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugport2getprocess"></a>IDebugPort2::GetProcess
Obtient le processus spécifié est en cours d’exécution sur un port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProcess(   
   AD_PROCESS_ID    ProcessId,  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(   
   AD_PROCESS_ID      ProcessId,  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ProcessId`  
 [in] Un [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure qui spécifie l’identificateur de processus.  
  
 `ppProcess`  
 [out] Retourne un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objet représentant le processus.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
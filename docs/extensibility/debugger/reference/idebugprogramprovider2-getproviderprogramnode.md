---
title: IDebugProgramProvider2::GetProviderProgramNode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b6984a89d39dc99351acaa0e37f2c3d9b1e47f1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117808"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Récupère le nœud de programme pour un programme spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```csharp  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Flags`  
 [in] Une combinaison d’indicateurs à partir de la [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) énumération. Les indicateurs suivants sont classiques pour cet appel :  
  
|Indicateur|Description|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|L’appelant est en cours d’exécution sur l’ordinateur distant.|  
|`PFLAG_DEBUGGEE`|L’appelant est en cours de débogage (informations supplémentaires sur le marshaling seront affichera pour chaque nœud).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|L’appelant a été attaché à mais pas lancé par le débogueur.|  
  
 `pPort`  
 [in] Le port, le processus appelant s’exécute sur.  
  
 `processId`  
 [in] Un [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure qui contient l’ID du processus qui contient le programme en question.  
  
 `guidEngine`  
 [in] GUID du moteur de débogage que le programme est attaché au (le cas échéant).  
  
 `programId`  
 [in] ID du programme pour lequel obtenir le nœud du programme.  
  
 `ppProgramNode`  
 [out] Un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objet représentant le nœud programme demandé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
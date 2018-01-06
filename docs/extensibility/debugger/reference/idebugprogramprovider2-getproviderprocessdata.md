---
title: IDebugProgramProvider2::GetProviderProcessData | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords: IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e94e0606256eda3fb8cdcade90979342d078e125
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Récupère une liste de programmes en cours d’exécution à partir d’un processus spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
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
|`PFLAG_GET_PROGRAM_NODES`|L’appelant demande une liste de nœuds de programme à retourner.|  
  
 `pPort`  
 [in] Le port, le processus appelant s’exécute sur.  
  
 `processId`  
 [in] Un [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure qui contient l’ID du processus qui contient le programme en question.  
  
 `EngineFilter`  
 [in] Un tableau de GUID pour les moteurs de débogage affectés pour déboguer ce processus (ils seront utilisés pour filtrer les programmes qui sont retournés en fonction de ce que les moteurs fournies prend en charge ; si aucun moteur n’est spécifiés, tous les programmes seront retourné).  
  
 `pProcess`  
 [out] A [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) structure est remplie avec les informations demandées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Normalement, cette méthode est appelée par un processus pour obtenir une liste des programmes en cours d’exécution dans ce processus. Les informations renvoyées sont une liste de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objets.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
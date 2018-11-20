---
title: IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 10a98502d432d454d8720ea637d906b6faa67978
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779630"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère une liste de programmes en cours d’exécution à partir d’un processus spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Flags`  
 [in] Une combinaison d’indicateurs de la [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) énumération. Les indicateurs suivants sont généralement utilisés pour cet appel :  
  
|Indicateur|Description|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|L’appelant est en cours d’exécution sur l’ordinateur distant.|  
|`PFLAG_DEBUGGEE`|L’appelant est en cours de débogage (informations supplémentaires sur le marshaling seront retournées pour chaque nœud).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|L’appelant a été attaché à mais pas lancé par le débogueur.|  
|`PFLAG_GET_PROGRAM_NODES`|L’appelant demande une liste de nœuds de programme à retourner.|  
  
 `pPort`  
 [in] Le port, le processus appelant s’exécute sur.  
  
 `processId`  
 [in] Un [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure qui contient l’ID du processus qui contient le programme en question.  
  
 `EngineFilter`  
 [in] Un tableau de GUID pour les moteurs de débogage affecté pour déboguer ce processus (ces seront utilisés pour filtrer les programmes qui sont en réalité retournées selon ce que les moteurs fournis en charge ; si aucun moteur n’est spécifié, tous les programmes seront retourné).  
  
 `pProcess`  
 [out] Un [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) structure est remplie avec les informations demandées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est généralement appelée par un processus pour obtenir une liste des programmes en cours d’exécution dans ce processus. Les informations retournées sont une liste de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objets.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)


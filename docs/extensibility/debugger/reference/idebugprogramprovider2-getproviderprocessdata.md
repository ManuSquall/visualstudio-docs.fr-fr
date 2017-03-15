---
title: "IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait une liste des programmes en cours de exécution d'un processus spécifié.  
  
## Syntaxe  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```c#  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### Paramètres  
 `Flags`  
 \[in\]  Une combinaison des indicateurs d'énumération de [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) .  Les balises suivantes sont courantes pour cet appel :  
  
|Indicateur|Description|  
|----------------|-----------------|  
|`PFLAG_REMOTE_PORT`|L'appelant s'exécute sur l'ordinateur distant.|  
|`PFLAG_DEBUGGEE`|L'appelant est en cours de débogage \(informations supplémentaires sur le marshaling seront retournées pour chaque nœud\).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|L'appelant a été attaché mais pas lancé par le débogueur.|  
|`PFLAG_GET_PROGRAM_NODES`|L'appelant demande une liste de nœuds de programme pour être retourné.|  
  
 `pPort`  
 \[in\]  Le port que le processus d'appel s'exécute.  
  
 `processId`  
 \[in\]  Une structure d' [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) maintenant l'ID du processus qui contient le programme en question.  
  
 `EngineFilter`  
 \[in\]  Un tableau de GUID pour les moteurs de débogage assignés pour déboguer ce processus \(qui seront utilisés pour filtrer les programmes qui sont retournés en fait suite à ce que le stockage de moteurs fourni ; si aucun moteur n'est spécifié, tous les programmes sont retournés\).  
  
 `pProcess`  
 \[out\]  Une structure de [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) remplie à l'aide de informations demandées.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est normalement appelée par un processus pour obtenir une liste des programmes qui s'exécutent dans ce processus.  les informations retournées sont une liste d'objets d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
## Voir aussi  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
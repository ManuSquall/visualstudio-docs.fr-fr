---
title: "IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère le nœud de programme pour un programme spécifique.  
  
## Syntaxe  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```c#  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
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
  
 `pPort`  
 \[in\]  Le port que le processus d'appel s'exécute.  
  
 `processId`  
 \[in\]  Une structure d' [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) maintenant l'ID du processus qui contient le programme en question.  
  
 `guidEngine`  
 \[in\]  GUID du moteur de débogage que le programme est attaché \(le cas échéant\).  
  
 `programId`  
 \[in\]  ID du programme pour lequel obtenir le nœud de programme.  
  
 `ppProgramNode`  
 \[out\]  Un objet d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) représentant le nœud demandé de programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
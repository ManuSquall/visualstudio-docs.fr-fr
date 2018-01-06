---
title: PROVIDER_FLAGS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_FLAGS
helpviewer_keywords: PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f6f2a1b57c627425ebf63c6068f358cb8be0d3c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="providerflags"></a>PROVIDER_FLAGS
Spécifie les propriétés souhaitées doivent être obtenues à partir d’un fournisseur de programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_PROVIDER_FLAGS {  
   PFLAG_NONE                    = 0x00,  
   PFLAG_REMOTE_PORT             = 0x01,  
   PFLAG_DEBUGGEE                = 0x02,  
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,  
   PFLAG_REASON_WATCH            = 0x08,  
   PFLAG_GET_PROGRAM_NODES       = 0x10,  
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20  
};  
typedef DWORD PROVIDER_FLAGS;  
```  
  
```csharp  
public enum enum_PROVIDER_FLAGS {  
   PFLAG_NONE                    = 0x00,  
   PFLAG_REMOTE_PORT             = 0x01,  
   PFLAG_DEBUGGEE                = 0x02,  
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,  
   PFLAG_REASON_WATCH            = 0x08,  
   PFLAG_GET_PROGRAM_NODES       = 0x10,  
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20  
};  
```  
  
## <a name="members"></a>Membres  
 PFLAG_NONE  
 Aucun indicateur n’est spécifié.  
  
 PFLAG_REMOTE_PORT  
 L’appelant souhaite obtenir une liste des programmes sur un autre ordinateur que [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 PFLAG_DEBUGGEE  
 Le processus est en cours de débogage par cette instance de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 PFLAG_ATTACH_TODEBUGGEE  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]n’est attaché au programme en cours de débogage, mais le n’a pas lancé.  
  
 PFLAG_REASON_WATCH  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]surveille les événements.  
  
 PFLAG_GET_PROGRAM_NODES  
 L’appelant veut le `ProgramNodes` champ le [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) structure.  
  
 PFLAG_GET_IS_DEBUGGER_PRESENT  
 L’appelant veut le `fIsTheDebuggerPresent` champ le `PROVIDER_PROCESS_DATA` structure.  
  
## <a name="remarks"></a>Notes  
 Ces indicateurs sont passés aux méthodes suivantes :  
  
-   [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)  
  
-   [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)  
  
-   [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)  
  
 Ces valeurs peuvent être combinées avec une opération de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
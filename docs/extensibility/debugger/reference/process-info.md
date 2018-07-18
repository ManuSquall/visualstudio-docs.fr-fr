---
title: PROCESS_INFO | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d35b94b6153b65672453ed8b4e7d2c0d9c2bd5eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134383"
---
# <a name="processinfo"></a>PROCESS_INFO
Contient des informations sur un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Membres  
 Champs  
 Une combinaison d’indicateurs à partir de la [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) énumération qui spécifient quels champs sont remplis.  
  
 bstrFileName  
 Le nom de chemin d’accès complet du processus. Équivalent à l’appel du [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) méthode avec le paramètre `GN_FILENAME`.  
  
 bstrBaseName  
 Le nom de fichier et l’extension du processus. Équivalent à l’appel du `IDebugProcess2::Getname` méthode avec le paramètre `GN_BASENAME`.  
  
 bstrTitle  
 Le titre du processus, s’il en existe. Équivalent à l’appel du `IDebugProcess2::Getname` méthode avec le paramètre `GN_TITLE`.  
  
 ProcessId  
 Le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure qui identifie le processus. Équivalent à l’appel du [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) (méthode).  
  
 dwSessionId  
 Identificateur de la session de débogage, ce processus est en cours d’exécution dans.  
  
 bstrAttachedSessionName  
 Le nom de la session attaché. Équivalent à l’appel du [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) (méthode).  
  
 CreationTime  
 Le processus a été créé.  
  
 Indicateurs  
 Une combinaison d’indicateurs à partir de la [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) énumération qui spécifient les propriétés du processus.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée à la [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) méthode où il est renseigné.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
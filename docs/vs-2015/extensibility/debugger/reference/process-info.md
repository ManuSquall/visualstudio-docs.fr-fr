---
title: PROCESS_INFO | Microsoft Docs
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
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b7d99110511f9d126c2545ae2917c67afffb361f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767125"
---
# <a name="processinfo"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Contient des informations relatives à un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Une combinaison d’indicateurs de la [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) énumération qui spécifient quels champs sont renseignés.  
  
 bstrFileName  
 Nom de chemin d’accès complet du processus. Équivalent à l’appel le [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) méthode avec le paramètre `GN_FILENAME`.  
  
 bstrBaseName  
 Le nom de fichier et l’extension du processus. Équivalent à l’appel le `IDebugProcess2::Getname` méthode avec le paramètre `GN_BASENAME`.  
  
 bstrTitle  
 Le titre du processus, le cas échéant. Équivalent à l’appel le `IDebugProcess2::Getname` méthode avec le paramètre `GN_TITLE`.  
  
 ProcessId  
 Le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure qui identifie le processus. Équivalent à l’appel le [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) (méthode).  
  
 dwSessionId  
 Identificateur de la session de débogage, ce processus est en cours d’exécution dans.  
  
 bstrAttachedSessionName  
 Le nom de la session attaché. Équivalent à l’appel le [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) (méthode).  
  
 CreationTime  
 Heure de création du processus.  
  
 Indicateurs  
 Une combinaison d’indicateurs de la [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) énumération qui spécifient les propriétés du processus.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée à la [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) méthode où il est renseigné.  
  
## <a name="requirements"></a>Configuration requise  
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


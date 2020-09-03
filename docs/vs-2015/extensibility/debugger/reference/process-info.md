---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ab05d85b55fd293b648603f067d135f703aff5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205019"
---
# <a name="process_info"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Contient des informations sur un processus.  
  
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
 Combinaison d’indicateurs de l’énumération [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) qui spécifie les champs à remplir.  
  
 bstrFileName  
 Nom de chemin d’accès complet du processus. Équivalent à l’appel de la méthode [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) avec le paramètre `GN_FILENAME` .  
  
 bstrBaseName  
 Nom de fichier et extension du processus. Équivalent à l’appel de la `IDebugProcess2::Getname` méthode avec le paramètre `GN_BASENAME` .  
  
 bstrTitle  
 Titre du processus, s’il en existe un. Équivalent à l’appel de la `IDebugProcess2::Getname` méthode avec le paramètre `GN_TITLE` .  
  
 ProcessId  
 Structure [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) qui identifie le processus. Équivalent à l’appel de la méthode [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) .  
  
 dwSessionId  
 Identificateur de la session de débogage dans laquelle ce processus s’exécute.  
  
 bstrAttachedSessionName  
 Nom de la session jointe. Équivalent à l’appel de la méthode [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) .  
  
 CreationTime  
 Heure à laquelle le processus a été créé.  
  
 Indicateurs  
 Combinaison d’indicateurs de l’énumération [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) qui spécifient les propriétés du processus.  
  
## <a name="remarks"></a>Notes  
 Cette structure est transmise à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) où elle est remplie.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

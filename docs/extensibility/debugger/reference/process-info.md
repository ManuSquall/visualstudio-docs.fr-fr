---
title: PROCESS_INFO | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 791686d7ab4516f5eb4da0642d97acb9df730f12
ms.lasthandoff: 02/22/2017

---
# <a name="processinfo"></a>PROCESS_INFO
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
  
```c#  
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
 Le titre du processus, le cas échéant. Équivalent à l’appel du `IDebugProcess2::Getname` méthode avec le paramètre `GN_TITLE`.  
  
 ProcessId  
 Le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure qui identifie le processus. Équivalent à l’appel du [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) (méthode).  
  
 dwSessionId  
 Identificateur de la session de débogage, ce processus est exécuté.  
  
 bstrAttachedSessionName  
 Le nom de session attaché. Équivalent à l’appel du [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) (méthode).  
  
 CreationTime  
 Heure de création du processus.  
  
 Indicateurs  
 Une combinaison d’indicateurs à partir de la [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) énumération qui spécifient les propriétés du processus.  
  
## <a name="remarks"></a>Remarques  
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

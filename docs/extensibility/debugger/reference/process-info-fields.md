---
title: PROCESS_INFO_FIELDS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROCESS_INFO_FIELDS
helpviewer_keywords: PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5732b287512cb14ab885619799d0c885f69b791
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Spécifié le type d’informations à récupérer pour un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>Membres  
 PIF_FILE_NAME  
 Initialisation/utiliser le `bstrFileName` champ le [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) structure.  
  
 PIF_BASE_NAME  
 Initialisation/utiliser le `bstrBaseName` champ le `PROCESS_INFO` structure.  
  
 PIF_TITLE  
 Initialisation/utiliser le `bstrTitle` champ le `PROCESS_INFO` structure.  
  
 PIF_PROCESS_ID  
 Initialisation/utiliser le `ProcessId` champ le `PROCESS_INFO` structure.  
  
 PIF_SESSION_ID  
 Initialisation/utiliser le `dwSessionId` champ le `PROCESS_INFO` structure.  
  
 PIF_ATTACHED_SESSION_NAME  
 Initialisation/utiliser le `bstrAttachedSessionName` champ le `PROCESS_INFO` structure.  
  
 PIF_CREATION_TIME  
 Initialisation/utiliser le `CreationTime` champ le `PROCESS_INFO` structure.  
  
 PIF_FLAGS  
 Initialisation/utiliser le `Flags` champ le `PROCESS_INFO` structure.  
  
 PIF_ALL  
 Remplit tous les champs.  
  
## <a name="remarks"></a>Remarques  
 Passé à la [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) méthode pour indiquer les champs de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) structure doivent être initialisées.  
  
 Également utilisé dans `Fields` champ le `PROCESS_INFO` structure pour indiquer les champs qui sont utilisés et valide.  
  
 Ces indicateurs peuvent être combinées avec une opération de bits `OR`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
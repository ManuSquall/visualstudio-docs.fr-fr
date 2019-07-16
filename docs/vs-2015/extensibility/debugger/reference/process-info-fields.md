---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7700670774dcb38b054cf28275f64c0c3046f741
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205025"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifié le type d’informations à récupérer pour un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
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
public enum enum_PROCESS_INFO_FIELDS {   
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
 Initialize/utiliser le `bstrFileName` champ la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) structure.  
  
 PIF_BASE_NAME  
 Initialize/utiliser le `bstrBaseName` champ la `PROCESS_INFO` structure.  
  
 PIF_TITLE  
 Initialize/utiliser le `bstrTitle` champ la `PROCESS_INFO` structure.  
  
 PIF_PROCESS_ID  
 Initialize/utiliser le `ProcessId` champ la `PROCESS_INFO` structure.  
  
 PIF_SESSION_ID  
 Initialize/utiliser le `dwSessionId` champ la `PROCESS_INFO` structure.  
  
 PIF_ATTACHED_SESSION_NAME  
 Initialize/utiliser le `bstrAttachedSessionName` champ la `PROCESS_INFO` structure.  
  
 PIF_CREATION_TIME  
 Initialize/utiliser le `CreationTime` champ la `PROCESS_INFO` structure.  
  
 PIF_FLAGS  
 Initialize/utiliser le `Flags` champ la `PROCESS_INFO` structure.  
  
 PIF_ALL  
 Remplit tous les champs.  
  
## <a name="remarks"></a>Notes  
 Passé à la [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) méthode pour indiquer les champs de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) structure doivent être initialisées.  
  
 Également utilisé dans `Fields` champ la `PROCESS_INFO` structure pour indiquer quels champs sont utilisés et valide.  
  
 Ces indicateurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)

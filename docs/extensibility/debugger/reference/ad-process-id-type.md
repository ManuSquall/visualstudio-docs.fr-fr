---
title: AD_PROCESS_ID_TYPE | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AD_PROCESS_ID_TYPE
helpviewer_keywords: AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3aa9720b64404eb2478763b36c04addb480babfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Indique comment interpréter un ID de processus dans le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>Membres  
 AD_PROCESS_ID_SYSTEM  
 ID de processus est un identificateur de système. Utilisez le `ProcessId.dwProcessId` champ le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure.  
  
 AD_PROCESS_ID_GUID  
 ID de processus est un GUID. Utilisez le `ProcessId.guidProcessId` champ le `AD_PROCESS_ID` structure.  
  
## <a name="remarks"></a>Notes  
 Utilisé pour le `ProcessIdType` membre de la [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure pour identifier le type d’ID de processus qui est contenue dans la structure. Détermine la manière d’interpréter le `ProcessId` union dans la structure.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
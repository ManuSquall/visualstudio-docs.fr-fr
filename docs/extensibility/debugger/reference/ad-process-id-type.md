---
title: AD_PROCESS_ID_TYPE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8318efdc64adf9792e44ccf2f4ad4aa9f74dd67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
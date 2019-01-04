---
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ee759f1b7a69c6813f48eeceb2e962effb1bfe6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986386"
---
# <a name="machineinfo"></a>MACHINE_INFO
Décrit un ordinateur particulier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```csharp  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## <a name="members"></a>Membres  
 `Fields`  
 Une combinaison d’indicateurs de la [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) énumération qui spécifient les champs de la structure sont initialisés.  
  
 `bstrName`  
 Le nom de l’ordinateur. Équivalent à l’appel [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).  
  
 `Flags`  
 Une combinaison d’indicateurs de la [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) énumération décrivant les attributs de l’ordinateur.  
  
## <a name="remarks"></a>Notes  
 Cette structure est retournée par un appel à la [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
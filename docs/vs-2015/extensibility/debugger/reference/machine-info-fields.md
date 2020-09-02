---
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cce5300a795922162f2e0b979e553f4235ceacc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147451"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie le type d’informations à récupérer pour un ordinateur particulier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## <a name="members"></a>Membres  
 MCIF_NAME  
 Initialisez/utilisez le `bstrName` champ de la structure.  
  
 MCIF_FLAGS  
 Initialisez/utilisez le `Flags` champ de la structure.  
  
 MIF_ALL  
 Initialisez/Utilisez tous les champs de la structure.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont passées à la méthode [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) pour indiquer les membres de la structure [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) qui doivent être initialisés.  
  
 Également utilisé dans le `Fields` membre de la `MACHINE_INFO` structure pour indiquer les champs qui sont utilisés et valides.  
  
 Ces indicateurs peuvent être combinés avec une opération au niveau du bit `OR` .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)

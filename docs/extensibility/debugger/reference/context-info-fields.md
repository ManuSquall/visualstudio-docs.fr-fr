---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 712876c38996b0e9b5f0b65cf0b0269d43b15907
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028428"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Spécifie les informations à récupérer sur un contexte de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Membres  
 CIF_MODULEURL  
 Initialize/utiliser le `bstrModuleUrl` champ la [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) structure.  
  
 CIF_FUNCTION  
 Initialize/utiliser le `bstrFunction` champ la `CONTEXT_INFO` structure.  
  
 CIF_FUNCTIONOFFSET  
 Initialize/utiliser le `posFunctionOffset` champ la `CONTEXT_INFO` structure.  
  
 CIF_ADDRESS  
 Initialize/utiliser le `bstrAddress` champ la `CONTEXT_INFO` structure.  
  
 CIF_ADDRESSOFFSET  
 Initialize/utiliser le `bstrAddressOffset` champ la `CONTEXT_INFO` structure.  
  
 CIF_ALLFIELDS  
 Initialize/utiliser tous les champs de la `CONTEXT_INFO` structure.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont passées à un paramètre à la [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) méthode pour indiquer les champs de la [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) structure doivent être initialisées.  
  
 Ces indicateurs sont également utilisées pour indiquer les champs de la `CONTEXT_INFO` structure sont utilisées et valide lors de la structure est retournée.  
  
 Ces valeurs peuvent être combinées avec une opération OR au niveau du bit.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
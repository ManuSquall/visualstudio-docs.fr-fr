---
title: CONTEXT_INFO_FIELDS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_INFO_FIELDS
helpviewer_keywords: CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e604dc09215ac98b2c23fe85312e281b306e9961
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Spécifie les informations à récupérer sur un contexte de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
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
 Initialisation/utiliser le `bstrModuleUrl` champ le [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) structure.  
  
 CIF_FUNCTION  
 Initialisation/utiliser le `bstrFunction` champ le `CONTEXT_INFO` structure.  
  
 CIF_FUNCTIONOFFSET  
 Initialisation/utiliser le `posFunctionOffset` champ le `CONTEXT_INFO` structure.  
  
 CIF_ADDRESS  
 Initialisation/utiliser le `bstrAddress` champ le `CONTEXT_INFO` structure.  
  
 CIF_ADDRESSOFFSET  
 Initialisation/utiliser le `bstrAddressOffset` champ le `CONTEXT_INFO` structure.  
  
 CIF_ALLFIELDS  
 Initialisation/utiliser tous les champs de la `CONTEXT_INFO` structure.  
  
## <a name="remarks"></a>Remarques  
 Ces valeurs sont passées à un paramètre à la [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) méthode pour indiquer les champs de la [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) structure doivent être initialisées.  
  
 Ces indicateurs sont également utilisés pour indiquer les champs de la `CONTEXT_INFO` structure sont utilisées et valide lors de la structure est retournée.  
  
 Ces valeurs peuvent être combinées avec une opération OR au niveau du bit.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
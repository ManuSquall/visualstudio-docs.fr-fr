---
title: BPRESI_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c589622678c3b499ac705c834348bdf38c6eae80
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879361"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie les informations à récupérer sur la résolution d’un point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membres  
 BPRESI_BPRESLOCATION  
 Initialize/utiliser le `bpResLocation` champ (emplacement de résolution de point d’arrêt) de la [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) structure.  
  
 BPRESI_PROGRAM  
 Initialize/utiliser le `pProgram` champ la `BP_RESOLUTION_INFO` structure.  
  
 BPRESI_THREAD  
 Initialize/utiliser le `pThread` champ la `BP_RESOLUTION_INFO` structure.  
  
 BPRESI_ALLFIELDS  
 Spécifie tous les champs.  
  
## <a name="remarks"></a>Notes  
 Passé à la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) méthode pour indiquer les champs de la [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) structure doivent être initialisées.  
  
 Ces indicateurs sont également utilisées pour indiquer les champs de la `BP_RESOLUTION_INFO` structure sont utilisées et valide lors de cette structure est retournée.  
  
 Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)


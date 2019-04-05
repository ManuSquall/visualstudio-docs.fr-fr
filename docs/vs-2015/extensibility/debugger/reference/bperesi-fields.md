---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1b5cba13e439c69b3502b00c6ae159b6af28178
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951951"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie les informations à récupérer sur la résolution d’un point d’arrêt ayant échouée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membres  
 PERESI_BPRESLOCATION  
 Initialize/utiliser le `bpResLocation` champ (emplacement de résolution de point d’arrêt) de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) structure.  
  
 BPERESI_PROGRAM  
 Initialize/utiliser le `pProgram` champ la `BP_ERROR_RESOLUTION_INFO` structure.  
  
 BPERESI_THREAD  
 Initialize/utiliser le `pThread` champ la `BP_ERROR_RESOLUTION_INFO` structure.  
  
 BPERESI_MESSAGE  
 Initialize/utiliser le `bstrMessage` champ la `BP_ERROR_RESOLUTION_INFO` structure.  
  
 BPERESI_TYPE  
 Initialize/utiliser le `dwType` champ (type de point d’arrêt) de la `BP_ERROR_RESOLUTION_INFO` structure.  
  
 BPERESI_ALLFIELDS  
 Initialize/utiliser tous les champs de la `BP_ERROR_RESOLUTION_INFO` structure.  
  
## <a name="remarks"></a>Notes  
 Passé en tant que paramètre à la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) méthode pour indiquer les champs de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) structure doivent être initialisées.  
  
 Ces valeurs sont également utilisées pour indiquer les champs dans le `BP_ERROR_RESOLUTION_INFO` structure sont utilisées et valide lors de cette structure est retournée.  
  
 Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)

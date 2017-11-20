---
title: BPERESI_FIELDS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BPERESI_FIELDS
helpviewer_keywords: BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e758309c10f9d5dace6a95337130599f34fdb76d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Spécifie les informations à récupérer sur une résolution d’échec d’un point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_BPERESI_FIELDS {   
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
public enum enum_BPERESI_FIELDS {   
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
 Initialisation/utiliser le `bpResLocation` champ (emplacement de résolution de point d’arrêt) de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) structure.  
  
 BPERESI_PROGRAM  
 Initialisation/utiliser le `pProgram` champ le `BP_ERROR_RESOLUTION_INFO` structure.  
  
 BPERESI_THREAD  
 Initialisation/utiliser le `pThread` champ le `BP_ERROR_RESOLUTION_INFO` structure.  
  
 BPERESI_MESSAGE  
 Initialisation/utiliser le `bstrMessage` champ le `BP_ERROR_RESOLUTION_INFO` structure.  
  
 BPERESI_TYPE  
 Initialisation/utiliser le `dwType` champ (type de point d’arrêt) de la `BP_ERROR_RESOLUTION_INFO` structure.  
  
 BPERESI_ALLFIELDS  
 Initialisation/utiliser tous les champs de la `BP_ERROR_RESOLUTION_INFO` structure.  
  
## <a name="remarks"></a>Remarques  
 Passé en tant que paramètre à la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) méthode pour indiquer les champs de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) structure doivent être initialisées.  
  
 Ces valeurs sont également utilisées pour indiquer quels champs de la `BP_ERROR_RESOLUTION_INFO` structure sont utilisés et valides lorsque cette structure est retournée.  
  
 Ces valeurs peuvent être combinées avec une opération de bits `OR`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
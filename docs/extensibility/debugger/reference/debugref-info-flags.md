---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9957b0aaf81048c5040e3f7ff54f3fa9be742dc1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858561"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Spécifie les informations à récupérer sur un objet de référence de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membres  
 DEBUGREF_INFO_NAME  
 Initialize/utiliser le `bstrName` champ dans la structure.  
  
 DEBUGREF_INFO_TYPE  
 Initialize/utiliser le `bstrType` champ dans la structure.  
  
 DEBUGREF_INFO_VALUE  
 Initialize/utiliser le `bstrValue` champ dans la structure.  
  
 DEBUGREF_INFO_ATTRIB  
 Initialize/utiliser le `dwAttrib` champ dans la structure.  
  
 DEBUGREF_INFO_REFTYPE  
 Initialize/utiliser le `dwRefType` champ dans la structure.  
  
 DEBUGREF_INFO_REF  
 Initialize/utiliser le `pReference` champ dans la structure.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 Le champ de valeur doit contenir la valeur auto-développé, s’il est disponible pour ce type d’objet.  
  
 DEBUGREF_INFO_NONE  
 Indique qu’aucun indicateur est défini.  
  
 DEBUGREF_INFO_ALL  
 Indique un masque des indicateurs.  
  
## <a name="remarks"></a>Notes  
 Ces indicateurs sont passées à la [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) et [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) méthodes pour indiquer les champs de la [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structure doivent être initialisées.  
  
 Utilisé pour le `dwFields` membre de la `DEBUG_REFERENCE_INFO` structure pour indiquer quels champs sont utilisés et valide lors de la structure est retournée.  
  
 Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
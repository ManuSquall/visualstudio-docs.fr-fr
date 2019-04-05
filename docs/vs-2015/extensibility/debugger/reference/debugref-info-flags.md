---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 05a073b3663ff85fe3d68878999aaf1dfa9e0017
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947998"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie les informations à récupérer sur un objet de référence de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
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
public enum enum_DEBUGREF_INFO_FLAGS {   
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
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)

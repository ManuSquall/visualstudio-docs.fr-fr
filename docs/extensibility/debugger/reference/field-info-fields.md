---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7e48ac549001ed8a6ef363540cf50affb0e7b605
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902504"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Spécifie les informations à récupérer sur un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Membres  
 FIF_FULLNAME  
 Initialize/utiliser le `bstrFullName` champ dans le [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) structure.  
  
 FIF_NAME  
 Initialize/utiliser le `bstrName` champ dans le `FIELD_INFO` structure.  
  
 FIF_TYPE  
 Initialize/utiliser le `bstrType` champ dans le `FIELD_INFO` structure.  
  
 FIF_MODIFIERS  
 Initialize/utiliser le `bstrModifiers` champ dans le `FIELD_INFO` structure.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont également passés en tant qu’argument à la [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) méthode pour spécifier les champs de la [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) structure doivent être initialisées.  
  
 Ces valeurs sont également utilisées dans le `dwFields` membre de la `FIELD_INFO` structure pour indiquer quels champs sont utilisés et valide.  
  
 Ces indicateurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
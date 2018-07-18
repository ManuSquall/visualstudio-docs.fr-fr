---
title: FIELD_INFO | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 180a968f642b8a4bf26e2e69d1d3ddff45dc1f25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104213"
---
# <a name="fieldinfo"></a>FIELD_INFO
Cette structure décrit une variable locale, paramètre ou autre champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```csharp  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>Membres  
 dwFields  
 Une combinaison d’indicateurs à partir de la [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) énumération qui indique quels membres sont renseignés.  
  
 bstrFullName  
 Le nom complet du champ.  
  
 bstrName  
 Le nom court du champ.  
  
 bstrType argument de type  
 Le type du champ.  
  
 dwModifiers  
 Une combinaison d’indicateurs à partir de la [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) énumération qui décrit le champ.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée à la [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) méthode où il est renseigné.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
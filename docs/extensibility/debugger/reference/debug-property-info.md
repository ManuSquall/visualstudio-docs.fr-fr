---
title: DEBUG_PROPERTY_INFO | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 3c1ce8a931ca8687056fcf161d78b7e40260e15f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
Contient des informations sur une propriété de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagDEBUG_PROPERTY_INFO {   
   DEBUGPROP_INFO_FLAGS dwValidFields;  
   BSTR                 bstrFullName;  
   BSTR                 bstrName;  
   BSTR                 bstrType;  
   BSTR                 bstrValue;  
   IDebugProperty2*     pProperty;  
   DBG_ATTRIB_FLAGS     dwAttrib;  
} DEBUG_PROPERTY_INFO;  
```  
  
```csharp  
public struct DEBUG_PROPERTY_INFO {   
   public uint            dwValidFields;  
   public string          bstrFullName;  
   public string          bstrName;  
   public string          bstrType;  
   public string          bstrValue;  
   public IDebugProperty2 pProperty;  
   public ulong           dwAttrib;  
};  
```  
  
## <a name="members"></a>Membres  
 dwValidFields  
 Une combinaison d’indicateurs à partir de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) énumération qui spécifie quels champs sont renseignés.  
  
 bstrFullName  
 Le nom complet de la propriété.  
  
 bstrName  
 Le nom de propriété dans un contexte.  
  
 bstrType argument de type  
 Le type de propriété sous forme de chaîne mise en forme.  
  
 bstrValue Argument de type  
 La valeur de propriété sous forme de chaîne mise en forme.  
  
 pProperty  
 Le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet décrit par cette structure.  
  
 dwAttrib  
 Une combinaison d’indicateurs à partir de la [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) énumération décrivant les attributs de cette propriété.  
  
## <a name="remarks"></a>Remarques  
 Une propriété est un objet de nature hiérarchique qui a un nom, le type et la valeur. Par exemple, une propriété peut décrire des variables locales, des paramètres, des variables espionnes et des expressions et des registres.  
  
 Cette structure est passée à la [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) méthode où il est renseigné. Cette structure est également retournée en tant que partie d’une liste de cette structure à partir de la [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) interface qui, à son tour, est retourné à partir d’un appel à la [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) et [ EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) méthodes.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)

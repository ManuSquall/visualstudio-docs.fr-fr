---
title: DEBUGPROP_INFO_FLAGS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUGPROP_INFO_FLAGS
helpviewer_keywords: DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24b0208cdfd49ef07ba85803d03a1e2c4aa91553
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Spécifie les informations à récupérer sur un objet de propriété de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membres  
 DEBUGPROP_INFO_FULLNAME  
 Initialisation/utiliser le `bstrFullName` champ.  
  
 DEBUGPROP_INFO_NAME  
 Initialisation/utiliser le `bstrName` champ.  
  
 DEBUGPROP_INFO_TYPE  
 Initialisation/utiliser le `bstrType` champ.  
  
 DEBUGPROP_INFO_VALUE  
 Initialisation/utiliser le `bstrValue` champ.  
  
 DEBUGPROP_INFO_ATTRIB  
 Initialisation/utiliser le `dwAttrib` champ.  
  
 DEBUGPROP_INFO_PROP,  
 Initialisation/utiliser le `pProperty` champ contenant une [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Spécifie que le champ de valeur doit contenir la valeur auto-développé, s’il est disponible pour ce type d’objet.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Obsolète.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Ne retournent pas des valeurs de (Embellir) ou des membres (autrement dit, ne mettez pas les valeurs).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Ne retournent pas des valeurs de synthèse spéciaux (par exemple, n’appelez pas `ToString()` sur un objet pour produire une valeur).  
  
 DEBUGPROP_INFO_NONE  
 Spécifie qu’aucun indicateur est défini.  
  
 DEBUGPROP_INFO_STANDARD  
 Initialisation/utiliser le `dwAttrib`, `bstrName`, `bstrType`, et `bstrValue` champs.  
  
 DEBUGPROP_INFO_All  
 Indique un masque de tous les indicateurs.  
  
## <a name="remarks"></a>Remarques  
 Ces valeurs sont passées à la [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), et [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) des méthodes pour indiquer les champs qui doivent être initialisées le [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structure.  
  
 Ces valeurs sont également utilisées pour le `dwFields` membre de la `DEBUG_PROPERTY_INFO` structure pour indiquer les champs de la structure sont utilisées et valide lors de la structure est retournée.  
  
 Ces valeurs peuvent être combinées avec une opération de bits `OR`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
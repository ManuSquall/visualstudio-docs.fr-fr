---
title: DEBUG_REFERENCE_INFO | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a528f73f0a13ab2702e35212a3ba00f8c8c13378
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103329"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
Décrit une référence.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```csharp  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## <a name="members"></a>Membres  
 dwFields  
 Une combinaison d’indicateurs à partir de la [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) énumération qui spécifie les champs sont remplis.  
  
 bstrName  
 Le nom spécifié par l’utilisateur de la [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet.  
  
 bstrType argument de type  
 Le type de référence sous forme de chaîne mise en forme.  
  
 bstrValue Argument de type  
 La valeur de référence sous forme de chaîne mise en forme  
  
 dwAttrib  
 Une combinaison d’indicateurs à partir de la [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) énumération qui spécifie les indicateurs pour les attributs de propriété de débogage.  
  
 dwRefType  
 Une valeur à partir de la [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) énumération qui spécifie si le type de référence est forte ou faible.  
  
 m_pReference  
 Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet qui spécifie les informations de référence.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée à un appel à la [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) (méthode) doit être renseigné. Cette structure est également retournée en tant que partie d’une liste à partir de la [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) interface qui, à son tour, est retourné à partir d’un appel à la [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
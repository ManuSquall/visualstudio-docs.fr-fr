---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
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
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 33a3f2a394ec46b92989d43b5efbd672fef05dc3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796634"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Décrit une référence.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Une combinaison d’indicateurs de la [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) énumération qui spécifie quels champs sont renseignés.  
  
 bstrName  
 Le nom spécifié par l’utilisateur de la [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet.  
  
 bstrType argument de type  
 Le type de référence sous forme de chaîne.  
  
 bstrValue Argument de type  
 La valeur de référence sous forme de chaîne  
  
 dwAttrib  
 Une combinaison d’indicateurs de la [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) énumération qui spécifie les indicateurs pour les attributs de propriété de débogage.  
  
 dwRefType  
 Une valeur comprise entre le [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) énumération qui spécifie si le type de référence est forte ou faible.  
  
 m_pReference  
 Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet qui spécifie les informations de référence.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée à un appel à la [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) méthode doit être renseigné. Cette structure est également retournée en tant que partie d’une liste à partir de la [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) interface qui, à son tour, est retourné à partir d’un appel à la [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
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


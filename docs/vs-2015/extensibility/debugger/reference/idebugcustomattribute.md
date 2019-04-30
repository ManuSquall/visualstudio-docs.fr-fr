---
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5db7f060e630c0b4175ecf4708f14fc03869e431
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568933"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un attribut personnalisé, et il peut fournir le nom, le parent et le type de classe de l’attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de symboles implémente cette interface pour prendre en charge les attributs personnalisés associés à un symbole. Elle est généralement implémentée sur son propre objet.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Un appel à [suivant](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) retourne cette interface. Un appel à la [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) méthode retourne le [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugCustomAttribute`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Obtient le champ auquel l’attribut actuel est attaché.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Obtient le type de classe d’attribut personnalisé.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Obtient le nom de l’attribut personnalisé.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Obtient les informations d’attribut comme un objet blob d’octets.|  
  
## <a name="remarks"></a>Notes  
 Un attribut personnalisé est une structure en c# qui fournit des métadonnées personnalisées associées à une classe particulière ou une méthode.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

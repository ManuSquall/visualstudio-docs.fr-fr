---
title: IDebugCustomAttribute Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31133139d0104cd29f5d0d0e760bd78ec5783fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732679"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Cette interface représente un attribut personnalisé, et elle peut fournir le nom, le parent et le type de classe de l’attribut.

## <a name="syntax"></a>Syntaxe

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface afin de prendre en charge les attributs personnalisés associés à un symbole. Il est généralement implémenté sur son propre objet.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) renvoie cette interface. Un appel à la méthode [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) renvoie l’interface [IEnumDebugCustomAttributes.](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugCustomAttribute`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Obtient le champ auquel l’attribut actuel est attaché.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Obtient le type de classe d’attribut personnalisé.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Obtient le nom de l’attribut personnalisé.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Obtient l’information d’attribut comme un blob d’octets.|

## <a name="remarks"></a>Notes
 Un attribut personnalisé est une structure pour Cmd qui fournit des métadonnées personnalisées associées à une classe ou une méthode particulière.

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

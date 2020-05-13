---
title: IEnumDebugCustomAttributes Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f8b521432124267d3f0e179d3a889fb599fa99d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717132"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Énumère les attributs personnalisés.

## <a name="syntax"></a>Syntaxe

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface pour prendre en charge les attributs personnalisés (via l’interface [IDebugCustomAttribute).](../../../extensibility/debugger/reference/idebugcustomattribute.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
- [EnumCustomAttributes renvoie](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugCustomAttributes`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Récupère un nombre précis d’attributs personnalisés dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Passe un nombre spécifié d’attributs personnalisés dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Obtient le nombre d’attributs personnalisés dans un enumérateur.|

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

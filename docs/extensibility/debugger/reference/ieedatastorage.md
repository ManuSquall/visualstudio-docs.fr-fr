---
title: IEEDataStorage ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad7da71d31e1093d87d68bb39958a71a117f5d5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718191"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Cette interface représente un éventail d’octets.

## <a name="syntax"></a>Syntaxe

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression (EE) implémente cette interface pour représenter un tableau d’octets (utilisé par des visualisateurs de type pour récupérer et modifier les données via l’interface [IPropertyProxyEESide).](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) L’EE implémente généralement cette interface pour prendre en charge les visualisateurs de type externe.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Les méthodes `IPropertyProxyEESide` de l’interface renvoient toutes cette interface. Appelez [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir l’interface [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Appelez [QueryInterface](/cpp/atl/queryinterface) sur une interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) pour obtenir l’interface [IPropertyProxyProvider.](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 L’interface `IEEDataStorage` implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Récupère le nombre spécifié d’octets de données à un tampon fourni.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Récupère le nombre d’octets de données disponibles.|

## <a name="remarks"></a>Notes
 Cette interface est utilisée par un visualiseur de type pour accéder aux données détenues par un objet spécifique. Les données sont traitées comme un tableau d’octets, permettant au visualisateur type de les manipuler de quelque manière que ce soit pour les présenter à l’utilisateur.

 Un visualiseur personnalisé peut également utiliser cette interface, si désiré, bien que plus généralement, un spectateur personnalisé utiliserait une interface personnalisée, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ou [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (pour les données axées sur les cordes).

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

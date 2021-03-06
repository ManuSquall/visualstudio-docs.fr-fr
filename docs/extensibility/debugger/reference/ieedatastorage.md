---
description: Cette interface représente un tableau d’octets.
title: IEEDataStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9434138114f2b4b0615e20c1b556ff6387c715de
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227331"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Cette interface représente un tableau d’octets.

## <a name="syntax"></a>Syntaxe

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression (EE) implémente cette interface pour représenter un tableau d’octets (utilisé par les visualiseurs de type pour récupérer et modifier des données via l’interface [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ). L’EE implémente généralement cette interface pour prendre en charge les visualiseurs de types externes.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Les méthodes sur l' `IPropertyProxyEESide` interface retournent toutes cette interface. Appelez [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir l’interface [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Appelez [QueryInterface](/cpp/atl/queryinterface) sur une interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) pour obtenir l’interface [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable
 L' `IEEDataStorage` interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Récupère le nombre spécifié d’octets de données dans une mémoire tampon fournie.|
|[GetSize,](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Récupère le nombre d’octets de données disponibles.|

## <a name="remarks"></a>Notes
 Cette interface est utilisée par un visualiseur de type pour accéder aux données détenues par un objet spécifique. Les données sont traitées comme un tableau d’octets, ce qui permet au visualiseur de type de le manipuler de la manière qui est nécessaire pour le présenter à l’utilisateur.

 Une visionneuse personnalisée peut également utiliser cette interface, si vous le souhaitez, bien que plus généralement, une visionneuse personnalisée utilise une interface personnalisée, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ou [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (pour les données orientées chaîne).

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

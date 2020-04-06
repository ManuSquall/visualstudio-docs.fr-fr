---
title: IDebugPropertyField - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a3f3c2dca16cd2c28c9d1727e4ac145c91c482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720699"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Cette interface fournit les fonctions qui permettent d’obtenir et de définir une propriété.

## <a name="syntax"></a>Syntaxe

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente [l’IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Cette interface est une spécialisation qui prend en charge le concept de propriétés sur une classe.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de l’interface [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si la méthode [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) revient `FIELD_KIND_PROP`.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes sur les interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Obtient la méthode qui obtient la propriété.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Obtient la méthode qui définit la propriété.|

## <a name="remarks"></a>Notes
 Une propriété est un concept de code géré et représente une méthode qui est traitée comme une variable. Les propriétés n’existent pas en C. non managéré.

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

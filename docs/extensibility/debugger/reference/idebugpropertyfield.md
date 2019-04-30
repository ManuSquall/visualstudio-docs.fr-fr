---
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c3376a6b8d6d269cac1f376e3f7f3f6f8a036f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916456"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Cette interface fournit les fonctions qui permettent d’obtenir et de définir une propriété.

## <a name="syntax"></a>Syntaxe

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente le [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Cette interface est une spécialisation qui prend en charge le concept de propriétés sur une classe.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de la [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface si le [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) méthode retourne `FIELD_KIND_PROP`.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaces, cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Obtient la méthode qui obtient la propriété.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Obtient la méthode qui définit la propriété.|

## <a name="remarks"></a>Notes
 Une propriété est un concept de code managé et représente une méthode qui est traitée comme une variable. Propriétés n’existent pas dans C++ non managé.

## <a name="requirements"></a>Configuration requise
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
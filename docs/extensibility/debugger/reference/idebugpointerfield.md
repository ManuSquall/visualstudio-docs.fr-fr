---
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff3ed7d23272bad1e047ddca46e20b4710644e30
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704447"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Cette interface représente un type de pointeur.

## <a name="syntax"></a>Syntaxe

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le fournisseur de symboles implémente cette interface pour représenter un pointeur.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de la [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retourne `FIELD_TYPE_POINTER`.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Outre les méthodes sur le `IDebugField` et `IDebugContainerField` interfaces, cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Retourne un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant la cible du pointeur.|

## <a name="remarks"></a>Notes
 En C/C++, un pointeur peut être un conteneur s’il est utilisé avec la notation de tableau. Par exemple, prenons `char *pString`, `pString` a un type de pointeur vers `char`. `pString[3]` a le type d’un conteneur qui est un pointeur vers `char` qui fait référence à la quatrième élément de ce conteneur.

## <a name="requirements"></a>Spécifications
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
---
description: Cette interface représente un type pointeur.
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 568e442f5294b3aaa4cd8c99d7bbd1f769581ca6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087741"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Cette interface représente un type pointeur.

## <a name="syntax"></a>Syntaxe

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le fournisseur de symboles implémente cette interface pour représenter un pointeur.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de l’interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retourne `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable
 Outre les méthodes sur les `IDebugField` `IDebugContainerField` interfaces et, cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Retourne un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant la cible du pointeur.|

## <a name="remarks"></a>Notes
 En C/C++, un pointeur peut être un conteneur s’il est utilisé avec la notation de tableau. Par exemple, donné `char *pString` , `pString` a un type de pointeur vers `char` . `pString[3]` a le type d’un conteneur qui est un pointeur vers `char` qui fait référence au quatrième élément de ce conteneur.

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

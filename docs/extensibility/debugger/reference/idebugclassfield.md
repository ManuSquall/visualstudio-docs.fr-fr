---
title: IDebugClassField - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b0e4cd7c851e65edf299f45ec97273804c25d8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734292"
---
# <a name="idebugclassfield"></a>IDebugClassField
Cette interface représente une classe en tant que type.

## <a name="syntax"></a>Syntaxe

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente l’interface [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Cette interface est une spécialisation qui représente un type de classe.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un certain nombre d’interfaces ont des méthodes qui peuvent retourner cette interface, y compris [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), et [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). En outre, vous pouvez utiliser [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de l’interface [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si la méthode [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retourne le drapeau `FIELD_TYPE_CLASS`.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes sur les interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) cette interface implémente ce qui suit :

|Méthode|Description|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Crée un enumérateur pour les classes de base de cette classe.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Détermine si une interface spécifique est définie dans la classe.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Crée un enumérateur pour les classes imbriquées de cette classe.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Obtient la classe qui entoure cette classe.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Crée un enumérateur pour les interfaces mises en œuvre par cette classe.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Crée un enumérateur pour les constructeurs de cette classe.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Obtient le nom de l’indexeur par défaut.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Crée un enumérateur pour lesumérateurs imbriqués de cette classe.|

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

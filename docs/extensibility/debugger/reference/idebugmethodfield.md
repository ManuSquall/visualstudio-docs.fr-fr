---
title: IDebugMethodField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061035933e57ea4ca8e7857f68ac3d6311bae32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727059"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Cette interface décrit une méthode.

## <a name="syntax"></a>Syntaxe

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente l’interface [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Cette interface est une spécialisation qui présente une méthode.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de l’interface [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retourne `FIELD_TYPE_METHOD` . En outre, les méthodes, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)et [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), retournent toutes l' `IDebugMethodField` interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes sur les interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Crée un énumérateur pour les paramètres de la méthode.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Obtient le pointeur « this » de l’objet contenant la méthode.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Crée un énumérateur pour toutes les variables locales de la méthode.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Crée un énumérateur pour les variables locales sélectionnées de la méthode.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Détermine si un attribut personnalisé spécifique a été défini.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Crée un énumérateur pour les variables locales statiques de la méthode.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Obtient le conteneur global de la méthode.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Crée un énumérateur pour le type de chaque argument requis pour appeler la méthode.|

## <a name="remarks"></a>Notes
 Une méthode peut contenir des paramètres ainsi que des variables locales.

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

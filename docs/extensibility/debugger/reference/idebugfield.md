---
title: IDebugField - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728757"
---
# <a name="idebugfield"></a>IDebugField
Cette interface représente un champ, c’est-à-dire une description d’un symbole ou d’un type.

## <a name="syntax"></a>Syntaxe

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface comme classe de base pour tous les champs.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est la classe de base pour tous les domaines. Basée sur la valeur de retour de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), cette interface peut retourner des interfaces plus spécialisées en utilisant [QueryInterface](/cpp/atl/queryinterface). En outre, de `IDebugField` nombreuses interfaces renvoient des objets de différentes méthodes.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugField`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtient des informations affichage sur le symbole ou le type.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Il a le genre de champ.|
|[Gettype](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Obtient le type de champ.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtient le conteneur du champ.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtient l’adresse du champ.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtient la taille d’un champ, dans les octets.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtient des informations étendues sur un champ.|
|[Égal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compare deux champs.|
|[GetTypeInfo (en anglais)](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtient des informations de type indépendante sur le symbole ou le type.|

## <a name="remarks"></a>Notes
 Un type est équivalent `typedef`à une langue C .

 Dans l’exemple de langue `weather` CMD suivant, `sunny` `stormy` est un type de classe, et sont des symboles :

```cpp
class weather;
weather sunny;
weather stormy;
```

 La question de savoir si un champ représente un symbole ou un type peut être déterminée en appelant [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) et en examinant le [résultat FIELD_KIND.](../../../extensibility/debugger/reference/field-kind.md) Si `FIELD_KIND_TYPE` le bit est réglé, le champ `FIELD_KIND_SYMBOL` est un type, et si le bit est réglé, c’est un symbole.

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)

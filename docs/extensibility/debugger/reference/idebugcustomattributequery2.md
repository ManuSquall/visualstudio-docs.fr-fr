---
description: Détermine l’existence d’un attribut personnalisé pour ce champ et, s’il existe, retourne les informations d’attribut.
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 62461cbdbfe373f6c3d45569564e611efdd6f452
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160223"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Détermine l’existence d’un attribut personnalisé pour ce champ et, s’il existe, retourne les informations d’attribut.

## <a name="syntax"></a>Syntaxe

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) afin de prendre en charge des attributs personnalisés.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de l’interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de l’interface **IDebugCustomAttributeQuery** .

|Méthode|Description|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Détermine si un attribut personnalisé existe par son nom.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Obtient les informations d’attribut pour l’attribut personnalisé donné.|

 En plus des méthodes **IDebugCustomAttributeQuery** , `IDebugCustomAttributeQuery2` implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Obtient un énumérateur pour tous les attributs personnalisés attachés à ce champ.|

## <a name="remarks"></a>Notes
 La méthode [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) peut retourner un énumérateur pour tous les attributs personnalisés définis pour ce champ.

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

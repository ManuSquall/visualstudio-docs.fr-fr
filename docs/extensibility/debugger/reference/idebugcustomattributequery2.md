---
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23f76cfc71fab73d5d31fe3f47c3f8c552271aa7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701028"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Détermine l’existence d’un attribut personnalisé pour ce champ et, si elle existe, retourne les informations d’attribut.

## <a name="syntax"></a>Syntaxe

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) pour prendre en charge les attributs personnalisés.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de la [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de la **IDebugCustomAttributeQuery** interface.

|Méthode|Description|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Détermine si un attribut personnalisé existe par nom.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Obtient les informations d’attribut pour l’attribut personnalisé.|

 Outre le **IDebugCustomAttributeQuery** méthodes, `IDebugCustomAttributeQuery2` implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Obtient un énumérateur pour tous les attributs personnalisés attachés à ce champ.|

## <a name="remarks"></a>Notes
 Le [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) méthode peut retourner un énumérateur pour tous les attributs personnalisés définis pour ce champ.

## <a name="requirements"></a>Spécifications
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
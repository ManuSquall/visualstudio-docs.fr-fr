---
title: IDebugContainerField - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72296517a64c6dcfcb8e347fb00588504aa75a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733215"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Cette interface représente un symbole ou un type qui est un conteneur pour d’autres symboles ou types.

## <a name="syntax"></a>Syntaxe

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente l’interface [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Cette interface est également la classe de base pour toutes les interfaces qui représentent des conteneurs.

## <a name="notes-for-callers"></a>Notes pour les appelants
 De nombreuses méthodes sur de nombreuses interfaces retournent cette interface. Parce qu’il s’agit d’une classe de base pour tous les conteneurs, des interfaces plus spécialisées peuvent obtenir à partir de cette interface en utilisant [QueryInterface](/cpp/atl/queryinterface). Ces interfaces incluent [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), et [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes de l’interface [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crée un enumérateur pour les champs du conteneur.|

## <a name="remarks"></a>Notes
 Les tableaux (conteneurs pour variables), les classes (conteneurs pour les méthodes et les variables) et les méthodes (conteneurs pour les paramètres et les variables locales) sont autant d’exemples de conteneurs.

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

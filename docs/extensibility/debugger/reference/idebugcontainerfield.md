---
description: Cette interface représente un symbole ou un type qui est un conteneur pour d’autres symboles ou types.
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 752eb7d77035a25ad1d0ddc8aec45afe95d898c7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154780"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Cette interface représente un symbole ou un type qui est un conteneur pour d’autres symboles ou types.

## <a name="syntax"></a>Syntaxe

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente l’interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Cette interface est également la classe de base pour toutes les interfaces qui représentent des conteneurs.

## <a name="notes-for-callers"></a>Notes pour les appelants
 De nombreuses méthodes sur de nombreuses interfaces retournent cette interface. Étant donné qu’il s’agit d’une classe de base pour tous les conteneurs, des interfaces plus spécialisées peuvent être obtenues à partir de cette interface à l’aide de [QueryInterface](/cpp/atl/queryinterface). Ces interfaces sont [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)et [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes sur l’interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crée un énumérateur pour les champs du conteneur.|

## <a name="remarks"></a>Notes
 Les tableaux (conteneurs pour les variables), les classes (conteneurs pour les méthodes et les variables) et les méthodes (conteneurs pour les paramètres et les variables locales) sont tous des exemples de conteneurs.

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

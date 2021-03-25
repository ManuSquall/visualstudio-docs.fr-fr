---
description: Cette interface est une interface d’extension implémentée par les implémenteurs IDebugProcess2.
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae5fb8766e9cd0f48e85fa0b060efb4faa7bc496
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076288"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Cette interface est une interface d’extension implémentée par les implémenteurs [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) . Il permet à l’implémenteur d’extraire des informations sur l’environnement du processus de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Implémentez cette interface pour obtenir des informations sur l’environnement d’exécution d’un processus de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProcessQueryProperties` .

|Méthode|Description|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Recherche une valeur de propriété.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Recherche des valeurs de propriété.|

## <a name="remarks"></a>Notes
 Cette interface est rarement implémentée.

## <a name="requirements"></a>Spécifications
 En-tête : Portpriv. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

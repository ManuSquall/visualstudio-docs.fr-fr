---
title: IDebugProcessQueryProperties ( france) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08abf401b4e8f0e7a33d882e8178d77e6f248318
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723280"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Cette interface est une interface d’extension implémentée par les implémenteurs [IDebugProcess2.](../../../extensibility/debugger/reference/idebugprocess2.md) Il permet à l’implémentateur d’obtenir des informations sur l’environnement de processus de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Implémentez cette interface pour obtenir des informations sur l’environnement d’exécution d’un processus de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugProcessQueryProperties`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Requêtes pour une valeur de propriété.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Requêtes pour la valeur des propriétés.|

## <a name="remarks"></a>Notes
 Cette interface est rarement implémentée.

## <a name="requirements"></a>Spécifications
 En-tête: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

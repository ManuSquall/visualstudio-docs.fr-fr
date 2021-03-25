---
description: Représente un alias numérique pour une variable et permet à un évaluateur d’expression (EE) d’obtenir le domaine d’application pour l’alias.
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ca97fbe23e9b0c84c39e591c0fd9cfb997fca5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059039"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Représente un alias numérique pour une variable et permet à un évaluateur d’expression (EE) d’obtenir le domaine d’application pour l’alias.

## <a name="syntax"></a>Syntaxe

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par le moteur DE débogage managé (DE).

## <a name="methods"></a>Méthodes
 Outre les méthodes sur l’interface [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) , cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Récupère l’identificateur pour le domaine d’application.|

## <a name="remarks"></a>Notes
 Un alias est un nombre décimal sous forme de chaîne suivi du caractère #, par exemple 1001 #.

## <a name="requirements"></a>Spécifications
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

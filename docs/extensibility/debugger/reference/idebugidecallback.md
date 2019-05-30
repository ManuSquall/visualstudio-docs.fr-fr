---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5a489256b14b828fd548b3e2da3c2c02f9d5317
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349566"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Permet à un évaluateur d’expression (EE) afficher un message dans la fenêtre de sortie du débogueur.

## <a name="syntax"></a>Syntaxe

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Ce rappel est implémenté par le moteur de débogage managé.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Il peut être consommé par un évaluateur d’expression pour envoyer la sortie à la fenêtre de sortie du débogueur.

## <a name="methods"></a>Méthodes
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Envoie la chaîne de message spécifié à la fenêtre de sortie du débogueur.|

## <a name="requirements"></a>Configuration requise
 En-tête : EE.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
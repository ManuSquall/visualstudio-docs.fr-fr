---
description: Active un évaluateur d’expression (EE) pour afficher un message dans la fenêtre sortie du débogueur.
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 461003f3bdb83e51e8b5c525895d134b717d8fc6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091901"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Active un évaluateur d’expression (EE) pour afficher un message dans la fenêtre sortie du débogueur.

## <a name="syntax"></a>Syntaxe

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Ce rappel est implémenté par le moteur de débogage managé.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Elle peut être consommée par un évaluateur d’expression pour envoyer la sortie vers la fenêtre de sortie du débogueur.

## <a name="methods"></a>Méthodes
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Envoie la chaîne de message spécifiée à la fenêtre de sortie du débogueur.|

## <a name="requirements"></a>Spécifications
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

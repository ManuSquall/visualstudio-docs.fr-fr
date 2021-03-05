---
description: Signale à l’interface utilisateur du débogueur Visual Studio d’avertir l’utilisateur que les symboles n’ont pas pu être localisés pour l’exécutable lancé.
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859c9c1d07a5f4660f2d13dcffac4f19659a2bc2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149819"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Signale [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] à l’interface utilisateur du débogueur d’avertir l’utilisateur que les symboles n’ont pas pu être localisés pour l’exécutable lancé.

## <a name="syntax"></a>Syntaxe

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Implémenté par les moteurs de débogage et consommé par l' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface utilisateur du débogueur.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

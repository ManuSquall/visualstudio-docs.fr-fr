---
description: Signale à l’interface utilisateur du débogueur Visual Studio d’avertir l’utilisateur que les symboles n’ont pas pu être localisés pour l’exécutable lancé.
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a060436575d51710fcef9c444ac843aa56195d0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058402"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Signale [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] à l’interface utilisateur du débogueur d’avertir l’utilisateur que les symboles n’ont pas pu être localisés pour l’exécutable lancé.

## <a name="syntax"></a>Syntaxe

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Implémenté par les moteurs de débogage et consommé par l' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface utilisateur du débogueur.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

---
title: Écriture d’une fonction de raccordement de débogage | Microsoft Docs
description: En savoir plus sur un certain nombre de fonctions de raccordement de débogage personnalisées que vous pouvez écrire pour vous permettre d’insérer votre code dans des points prédéfinis à l’intérieur du traitement normal du débogueur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76727da1ed057902d8f757594f5ed2e07bcf3cea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857543"
---
# <a name="debug-hook-function-writing"></a>Écriture de fonctions de raccordement de débogage
Cette section décrit plusieurs fonctions de raccordement de débogage personnalisées que vous pouvez écrire pour vous permettre d'insérer votre code dans quelques points prédéfinis du traitement normal du débogueur.

## <a name="in-this-section"></a>Dans cette section
 [Fonctions de raccordement de bloc client](../debugger/client-block-hook-functions.md) Fournit des conseils et un prototype pour l’écriture de fonctions qui valident ou signalent le contenu des données stockées dans des blocs _CLIENT_BLOCK.

 [Fonctions de raccordement d’allocation](../debugger/allocation-hook-functions.md) Définit une fonction de raccordement d’allocation, explore ses différentes utilisations, présente des restrictions et fournit un prototype.

 [Raccordements d’allocation et allocations de mémoire CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) Décrit la restriction sur les fonctions de raccordement d’allocation de blocs ignorés explicitement `_CRT_BLOCK` s’ils effectuent des appels à des fonctions de la bibliothèque Runtime C qui allouent de la mémoire interne. Cette rubrique répertorie également les conséquences si votre raccordement d’allocation n’ignore pas les blocs `_CRT_BLOCK` (avec exemples) et la façon de modifier la fonction de raccordement d’allocation par défaut, **CrtDefaultAllocHook**.

 [Fonctions de raccordement de rapport](../debugger/report-hook-functions.md) Aborde `_CrtSetReportHook` les, que vous pouvez utiliser pour filtrer des rapports afin de vous concentrer sur des types d’allocation spécifiques. Cette rubrique fournit également un prototype.

## <a name="related-sections"></a>Sections connexes

- [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md) : liens vers les techniques de débogage pour la bibliothèque C Run-Time, y compris l’utilisation de la bibliothèque de débogage CRT, les macros pour la création de rapports, les différences entre `malloc` et `_malloc_dbg` , l’écriture de fonctions de raccordement de débogage et le tas de débogage CRT.
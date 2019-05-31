---
title: Déboguer les violations d’accès lorsque vous exécutez l’application en dehors du débogueur
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d42dd206117885a23a6c1c15c712be4dc4cd8fe2
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177665"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Comment puis-je déboguer les violations d'accès lorsque mon programme fonctionne hors du débogueur ?

## <a name="problem-description"></a>Description du problème
 Mon programme fonctionne correctement dans l'environnement Visual Studio, mais lorsque je l'exécute de façon autonome avec le système d'exploitation Windows, il génère une violation d'accès. Comment puis-je corriger cette erreur ?

## <a name="solution"></a>Solution
 Paramétrez l’option [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md) et exécutez votre programme de façon autonome jusqu’à ce que la violation d’accès se produise. Dans la boîte de dialogue **Violation d’accès**, vous pouvez ensuite cliquer sur **Annuler** afin de démarrer le débogueur.

## <a name="see-also"></a>Voir aussi
- [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
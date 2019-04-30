---
title: Utiliser les fenêtres du débogueur pendant le débogage d’une application de premier plan | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11bd61cda8c92721fb42c640b0b5100b8054acdf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894864"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Comment puis-je utiliser les fenêtres du débogueur pendant le débogage d'un programme d'avant-plan ?
## <a name="problem-description"></a>Description du problème
 J'essaie de corriger un problème de peinture de l'écran. Pour observer ce problème, je dois conserver mon programme au premier plan. Autrement dit, je n'ai pas accès aux fenêtres de débogage. Que puis-je faire ?

## <a name="solution"></a>Solution
 Si vous disposez d'un autre ordinateur, vous pouvez recourir au débogage distant. Dans une installation comportant deux ordinateurs, vous pouvez observer la peinture de l'écran sur l'ordinateur distant, tout en utilisant le débogueur sur l'hôte. Pour plus d’informations sur le débogage à distance, consultez [le débogage à distance](../debugger/remote-debugging.md).

## <a name="see-also"></a>Voir aussi
- [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
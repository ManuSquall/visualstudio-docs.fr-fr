---
title: Utiliser les fenêtres du débogueur lors du débogage d’une application de premier plan | Microsoft Docs
Description: Si vous déboguez un programme qui doit rester au premier plan, utilisez le débogage distant pour éviter de le placer en arrière-plan.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 420a4073e4c00f66775bf55565c2ee8645d90f49
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911370"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Comment puis-je utiliser les fenêtres du débogueur pendant le débogage d'un programme d'avant-plan ?
## <a name="problem-description"></a>Description du problème
 J'essaie de corriger un problème de peinture de l'écran. Pour observer ce problème, je dois conserver mon programme au premier plan. Autrement dit, je n'ai pas accès aux fenêtres de débogage. Que puis-je faire ?

## <a name="solution"></a>Solution
 Si vous disposez d'un autre ordinateur, vous pouvez recourir au débogage distant. Dans une installation comportant deux ordinateurs, vous pouvez observer la peinture de l'écran sur l'ordinateur distant, tout en utilisant le débogueur sur l'hôte. Pour plus d’informations sur le débogage distant, consultez [débogage distant](../debugger/remote-debugging.md).

## <a name="see-also"></a>Voir aussi
- [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
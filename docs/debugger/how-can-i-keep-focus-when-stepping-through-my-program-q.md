---
title: Conserver le focus lorsque j’effectue un pas à pas détaillé dans mon application | Microsoft Docs
Description: Utilisez le débogage distant pour empêcher votre programme de perdre le focus quand vous déboguez un problème d’activation de la fenêtre.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.stepping
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], stepping
- focus, keeping
- stepping, focus
- windows, troubleshooting activation
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b821c374a87983ab8cb2667b434b1509e8449f31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911440"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-app"></a>Comment puis-je conserver le focus lorsque j’effectue un pas à pas détaillé dans mon application ?
## <a name="description"></a>Description
 Mon programme a un problème d'activation des fenêtres. Lorsque j'exécute mon programme en pas à pas avec le débogueur, je ne parviens pas à reproduire le problème, car le programme continue de perdre le focus. Existe-t-il un moyen d'éviter cela ?

## <a name="solution"></a>Solution
 Si vous disposez d'un autre ordinateur, utilisez le débogage distant. Vous pouvez faire fonctionner votre programme sur l'ordinateur distant pendant que vous exécutez le débogueur sur l'hôte. Pour plus d’informations, consultez [Comment : sélectionner un ordinateur distant](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100)).

## <a name="see-also"></a>Voir aussi
- [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Joindre aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
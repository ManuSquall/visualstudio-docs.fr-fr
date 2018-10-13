---
title: Comment puis-je utiliser les fenêtres du débogueur pendant le débogage d'un programme d'avant-plan ? | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.background
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 296cb0da8615e07c4f7cb22e76b81d6819a8f816
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286505"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Comment puis-je utiliser les fenêtres du débogueur pendant le débogage d'un programme d'avant-plan ?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Description du problème  
 J'essaie de corriger un problème de peinture de l'écran. Pour observer ce problème, je dois conserver mon programme au premier plan. Autrement dit, je n'ai pas accès aux fenêtres de débogage. Que puis-je faire ?  
  
## <a name="solution"></a>Solution  
 Si vous disposez d'un autre ordinateur, vous pouvez recourir au débogage distant. Dans une installation comportant deux ordinateurs, vous pouvez observer la peinture de l'écran sur l'ordinateur distant, tout en utilisant le débogueur sur l'hôte. Pour plus d’informations sur le débogage à distance, consultez [configuration du débogage distant](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)




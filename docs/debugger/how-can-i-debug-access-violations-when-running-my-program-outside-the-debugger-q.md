---
title: "Comment puis-je déboguer les violations d'accès lorsque mon programme fonctionne hors du débogueur ? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9b78b679878a68505162b6edd3fcd23403c8d07c
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2018
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Comment puis-je déboguer les violations d'accès lorsque mon programme fonctionne hors du débogueur ?
## <a name="problem-description"></a>Description du problème  
 Mon programme fonctionne correctement dans l'environnement Visual Studio, mais lorsque je l'exécute de façon autonome avec le système d'exploitation Windows, il génère une violation d'accès. Comment puis-je corriger cette erreur ?  
  
## <a name="solution"></a>Solution  
 Définir le [juste-à-temps débogage](../debugger/just-in-time-debugging-in-visual-studio.md) option et exécuter votre programme de façon autonome jusqu'à ce que la violation d’accès se produit. Puis, dans le **Violation d’accès** boîte de dialogue, vous pouvez cliquer sur **Annuler** pour démarrer le débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [Foire aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
---
title: "Comment puis-je déboguer les violations d'accès lorsque mon programme fonctionne hors du débogueur ? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b8a6e019725f95788b4988fbe1ddef18cb27cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Comment puis-je déboguer les violations d'accès lorsque mon programme fonctionne hors du débogueur ?
## <a name="problem-description"></a>Description du problème  
 Mon programme fonctionne correctement dans l'environnement Visual Studio, mais lorsque je l'exécute de façon autonome avec le système d'exploitation Windows, il génère une violation d'accès. Comment puis-je corriger cette erreur ?  
  
## <a name="solution"></a>Solution  
 Définir le [juste-à-temps débogage](../debugger/just-in-time-debugging-in-visual-studio.md) option et exécuter votre programme de façon autonome jusqu'à ce que la violation d’accès se produit. Puis, dans le **Violation d’accès** boîte de dialogue, vous pouvez cliquer sur **Annuler** pour démarrer le débogueur.  
  
 Consultez également, dans la Base de connaissances, l'article Q133174, « How to Locate Where a General Protection (GP) Fault Occurs ». Vous trouverez les articles de la Base de connaissances sur le CD-ROM MSDN Library ou en recherchant [http://support.microsoft.com/](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Voir aussi  
 [Foire aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
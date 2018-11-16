---
title: Comment puis-je déboguer les violations d'accès lorsque mon programme fonctionne hors du débogueur ? | Microsoft Docs
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
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e0ed8025986c92cd4c809ea8b04f0109fb010c5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816273"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Comment puis-je déboguer les violations d'accès lorsque mon programme fonctionne hors du débogueur ?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Description du problème  
 Mon programme fonctionne correctement dans l'environnement Visual Studio, mais lorsque je l'exécute de façon autonome avec le système d'exploitation Windows, il génère une violation d'accès. Comment puis-je corriger cette erreur ?  
  
## <a name="solution"></a>Solution  
 Définir le [juste-à-temps débogage](../debugger/just-in-time-debugging-in-visual-studio.md) option et exécuter votre programme de façon autonome jusqu'à ce que la violation d’accès se produit. Ensuite, dans le **Violation d’accès** boîte de dialogue, vous pouvez cliquer sur **Annuler** pour démarrer le débogueur.  
  
 Consultez également, dans la Base de connaissances, l'article Q133174, « How to Locate Where a General Protection (GP) Fault Occurs ». Vous trouverez les articles de la Base de connaissances sur le CD MSDN Library ou en effectuant une recherche [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)




---
title: Comment puis-je déboguer les violations d'accès lorsque mon programme fonctionne hors du débogueur ? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 7cfdf356d21558f2024cb83e00bdfc930284b1d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164107"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Comment puis-je déboguer les violations d'accès lorsque mon programme fonctionne hors du débogueur ?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Description du problème  
 Mon programme fonctionne correctement dans l'environnement Visual Studio, mais lorsque je l'exécute de façon autonome avec le système d'exploitation Windows, il génère une violation d'accès. Comment puis-je corriger cette erreur ?  
  
## <a name="solution"></a>Solution  
 Paramétrez l’option [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md) et exécutez votre programme de façon autonome jusqu’à ce que la violation d’accès se produise. Dans la boîte de dialogue **Violation d’accès**, vous pouvez ensuite cliquer sur **Annuler** afin de démarrer le débogueur.  
  
 Consultez également, dans la Base de connaissances, l'article Q133174, « How to Locate Where a General Protection (GP) Fault Occurs ». Vous trouverez les articles de la Base de connaissances sur le CD MSDN Library ou en effectuant une recherche [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Voir aussi  
 [Questions fréquentes (FAQ) sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)

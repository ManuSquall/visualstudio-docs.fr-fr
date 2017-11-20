---
title: "Boîte de dialogue (Exception levée) du débogueur Microsoft Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adda9e64a911a8a5119d28f97d3e2424710367d7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Débogueur Microsoft Visual Studio (Exception levée) (boîte de dialogue)
Une exception s'est produite dans votre programme. Cette boîte de dialogue indique le type d'exception levé. Votre code doit gérer cette exception. Pour ce faire, vous avez le choix entre les options suivantes :  
  
 **Break**  
 Autorise l'arrêt de l'exécution dans le débogueur. Le gestionnaire d'exceptions n'est pas appelé avant l'arrêt. Si vous poursuivez l'exécution après l'arrêt, le gestionnaire d'exceptions est appelé.  
  
 **Continue**  
 Autorise la poursuite de l'exécution en donnant au gestionnaire d'exceptions une chance de traiter cette exception. Cette option n'est pas disponible pour certains types d'exceptions. **Continuer** permet à l’application continuer. Dans une application native, l'exception est de nouveau levée. Dans une application managée, cela entraîne l'arrêt du programme ou la gestion de l'exception par une application hôte.  
  
> [!NOTE]
>  Vous ne pouvez pas continuer l'exécution à la suite de la levée d'une exception non traitée dans du code managé. En choisissant **continuer** après une exception non gérée dans le code managé arrêter le débogage.  
  
 **Ignorer**  
 Autorise la poursuite de l'exécution sans appeler le gestionnaire d'exceptions. Comme le gestionnaire d'exceptions n'est pas appelé, il risque de s'ensuivre des conséquences indésirables, notamment de nouvelles exceptions et des erreurs. Cette option n'est pas disponible pour certains types d'exceptions.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)   
 [Meilleures pratiques pour les exceptions](/dotnet/standard/exceptions/best-practices-for-exceptions)   
 [Gestion des exceptions](/cpp/windows/exception-handling-cpp-component-extensions)
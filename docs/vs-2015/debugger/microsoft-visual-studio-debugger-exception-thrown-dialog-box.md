---
title: Boîte de dialogue (Exception levée) du débogueur Microsoft Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3fec8fd6bc00199fc2a0d5193d7f7534acca754
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383938"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Débogueur Microsoft Visual Studio (Exception levée) (boîte de dialogue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une exception s'est produite dans votre programme. Cette boîte de dialogue indique le type d'exception levé. Votre code doit gérer cette exception. Pour ce faire, vous avez le choix entre les options suivantes :  
  
 **Break**  
 Autorise l'arrêt de l'exécution dans le débogueur. Le gestionnaire d'exceptions n'est pas appelé avant l'arrêt. Si vous poursuivez l'exécution après l'arrêt, le gestionnaire d'exceptions est appelé.  
  
 **Continue**  
 Autorise la poursuite de l'exécution en donnant au gestionnaire d'exceptions une chance de traiter cette exception. Cette option n'est pas disponible pour certains types d'exceptions. **Continue** autorise l’application à continuer. Dans une application native, l'exception est de nouveau levée. Dans une application managée, cela entraîne l'arrêt du programme ou la gestion de l'exception par une application hôte.  
  
> [!NOTE]
> Vous ne pouvez pas continuer l'exécution à la suite de la levée d'une exception non traitée dans du code managé. Si vous sélectionnez **Continue** après une exception non gérée dans du code managé, le débogage s’arrête.  
  
 **Ignore**  
 Autorise la poursuite de l'exécution sans appeler le gestionnaire d'exceptions. Comme le gestionnaire d'exceptions n'est pas appelé, il risque de s'ensuivre des conséquences indésirables, notamment de nouvelles exceptions et des erreurs. Cette option n'est pas disponible pour certains types d'exceptions.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)   
 [Meilleures pratiques pour les exceptions](http://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Gestion des exceptions](http://msdn.microsoft.com/library/ccb11fe8-6938-41ac-b477-a183e85865b9)

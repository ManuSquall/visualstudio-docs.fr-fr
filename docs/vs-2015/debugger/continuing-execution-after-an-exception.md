---
title: Continuer l’exécution après une Exception | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 947a17993fe0e8366149d1cef79c26c68b11d22a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730030"
---
# <a name="continuing-execution-after-an-exception"></a>Poursuite de l'exécution à la suite d'une exception
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque le débogueur arrête l'exécution à cause d'une exception, une boîte de dialogue apparaît. Pour Visual Basic ou c#, vous verrez la [Assistant Exception](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) boîte de dialogue, par défaut. Pour C++, vous verrez l’ancien **Exception** boîte de dialogue. Si vous utilisez Visual Basic ou c# mais que vous avez désactivé la **Assistant Exception** dans le **Options** boîte de dialogue, vous verrez la **Exception** boîte de dialogue.  
  
 Lorsque le **Assistant Exception** ou **Exception** boîte de dialogue s’affiche, vous pouvez essayer de résoudre le problème qui a provoqué l’exception.  
  
## <a name="managed-code"></a>Code managé  
 Dans le code managé, il est possible de poursuivre l'exécution dans le même thread à la suite d'une exception non gérée. Le **Assistant Exception** se déroule la pile des appels au point où l’exception a été levée.  
  
## <a name="native-code"></a>Code natif  
 En C/C++ natif, vous avez deux options :  
  
-   Vous pouvez cliquer sur **rompre** et essayer de résoudre le problème. Lorsque vous êtes en mode arrêt, vous pouvez dérouler la pile des appels en cliquant sur un frame dans la **pile des appels** fenêtre et en sélectionnant **dérouler sur ce Frame** dans le menu contextuel. Si vous continuez à déboguer, le **Exception** boîte de dialogue s’affiche à nouveau si vous n’avez pas résolu le problème. Sinon, le **Exception** boîte de dialogue ne réapparaisse pas.  
  
-   Vous pouvez cliquer sur **continuer** pour continuer l’exécution sans essayer de résoudre le problème. Le **Exception** boîte de dialogue réapparaît.  
  
## <a name="mixed-code"></a>Code mixte  
 Si une exception non gérée se produit durant le débogage d'un code mixte natif et managé, les contraintes du système d'exploitation empêchent le déroulement de la pile des appels. Si vous essayez de rembobiner la pile des appels via le menu contextuel, un message d'erreur explique que le débogueur ne peut pas dérouler à partir d'une exception non gérée lors du débogage de code mixte.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)






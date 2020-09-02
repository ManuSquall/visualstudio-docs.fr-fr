---
title: Poursuite de l’exécution après une exception | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702268"
---
# <a name="continuing-execution-after-an-exception"></a>Poursuite de l'exécution à la suite d'une exception
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque le débogueur arrête l'exécution à cause d'une exception, une boîte de dialogue apparaît. Pour Visual Basic ou C#, la boîte de dialogue [Assistant Exception](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) s’affiche par défaut. Pour C++, vous verrez la plus ancienne boîte de dialogue d' **exception** . Si vous utilisez Visual Basic ou C#, mais que vous avez désactivé l' **Assistant Exception** dans la boîte de dialogue **options** , la boîte de dialogue d' **exception** s’affiche.  
  
 Lorsque l' **Assistant Exception** ou la boîte de dialogue d' **exception** s’affiche, vous pouvez essayer de résoudre le problème à l’origine de l’exception.  
  
## <a name="managed-code"></a>Code managé  
 Dans le code managé, il est possible de poursuivre l'exécution dans le même thread à la suite d'une exception non gérée. L' **Assistant Exception** déroule la pile des appels jusqu’au point où l’exception a été levée.  
  
## <a name="native-code"></a>Code natif  
 En C/C++ natif, vous avez deux options :  
  
- Vous pouvez cliquer sur **arrêter** et essayer de résoudre le problème. Lorsque vous êtes en mode arrêt, vous pouvez dérouler la pile des appels en cliquant avec le bouton droit sur un frame dans la fenêtre **pile des appels** et en sélectionnant **dérouler sur ce frame** dans le menu contextuel. Lorsque vous continuez le débogage, la boîte de dialogue d' **exception** s’affiche à nouveau si vous n’avez pas résolu le problème. Dans le cas contraire, la boîte de dialogue d' **exception** ne réapparaîtra pas.  
  
- Vous pouvez cliquer sur **Continuer** pour continuer l’exécution sans tenter de résoudre le problème. La boîte de dialogue d' **exception** réapparaît.  
  
## <a name="mixed-code"></a>Code mixte  
 Si une exception non gérée se produit durant le débogage d'un code mixte natif et managé, les contraintes du système d'exploitation empêchent le déroulement de la pile des appels. Si vous essayez de rembobiner la pile des appels via le menu contextuel, un message d'erreur explique que le débogueur ne peut pas dérouler à partir d'une exception non gérée lors du débogage de code mixte.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)

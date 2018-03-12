---
title: "Continuer l’exécution après une Exception | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
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
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 84ade967c00e33390402e16a1b2980277f89ed5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="continuing-execution-after-an-exception"></a>Poursuite de l'exécution à la suite d'une exception
Lorsque le débogueur arrête l’exécution en raison d’une exception, vous verrez la **assistance d’Exception**, par défaut. Si vous avez désactivé la **assistance d’Exception** dans le **Options** boîte de dialogue, vous verrez la **Assistant Exception** (c# ou Visual Basic) ou le **(Exception)**  boîte de dialogue (C++).  
  
 Lorsque le **assistance d’Exception** s’affiche, vous pouvez tenter de résoudre le problème qui a provoqué l’exception.
  
## <a name="managed-and-native-code"></a>Code managé et natif  
 Dans le code managé et natif, vous pouvez poursuivre l’exécution dans le même thread après une exception non gérée. Le **assistance d’Exception** se déroule la pile des appels au point où l’exception a été levée.
  
## <a name="mixed-code"></a>Code mixte  
 Si une exception non gérée se produit durant le débogage d'un code mixte natif et managé, les contraintes du système d'exploitation empêchent le déroulement de la pile des appels. Si vous essayez de rembobiner la pile des appels via le menu contextuel, un message d'erreur explique que le débogueur ne peut pas dérouler à partir d'une exception non gérée lors du débogage de code mixte.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)
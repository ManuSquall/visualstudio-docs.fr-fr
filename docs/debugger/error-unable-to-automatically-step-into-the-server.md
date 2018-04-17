---
title: 'Erreur : Impossible d’automatiquement une étape dans le serveur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7fb8d7eeacf8ab4a4eccf94574e0b3911019db9e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Erreur : Impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur
L’erreur affiche le message suivant :  
  
 Impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur. Le débogueur n’a pas été notifié avant l’exécution de la procédure distante.  
  
 Cette erreur peut se produire lorsque vous essayez d’effectuer un pas à pas détaillé dans un service Web (consultez [Exécution pas à pas d’un service Web XML](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Elle peut survenir toute les fois que [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n’est pas installé correctement.  
  
 Causes possibles :  
  
-   Le fichier web.config pour votre application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n’affecte pas la valeur "true" au débogage (consultez [Mode débogage dans les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Une version de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a été installée après l’installation de Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] doit être installé avant Visual Studio. Pour résoudre ce problème, utilisez les fenêtres **le panneau de configuration > Programmes et fonctionnalités** pour réparer votre installation de Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Débogage à distance](../debugger/remote-debugging.md)
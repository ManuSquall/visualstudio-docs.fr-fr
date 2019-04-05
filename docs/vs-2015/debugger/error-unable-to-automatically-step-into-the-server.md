---
title: 'Erreur : Impossible de pas à pas automatiquement le serveur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.causality_no_server_response
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
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b12509de2e2ba536d9d54d11a41924d86bf5667
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951804"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Erreur : Impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’erreur affiche le message suivant :  
  
 Impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur. Le débogueur n’a pas été notifié avant l’exécution de la procédure distante.  
  
 Cette erreur peut se produire lorsque vous essayez d’effectuer un pas à pas détaillé dans un service Web (consultez [Exécution pas à pas d’un service Web XML](http://msdn.microsoft.com/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Elle peut survenir toute les fois que [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] n’est pas installé correctement.  
  
 Causes possibles :  
  
-   Le fichier web.config pour votre application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] n’affecte pas la valeur "true" au débogage (consultez [Mode débogage dans les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Une version de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] a été installée après l’installation de Visual Studio. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] doit être installé avant Visual Studio. Pour résoudre ce problème, dans le **Panneau de configuration**Windows, accédez à **Programmes et Fonctionnalités** afin de réparer votre installation Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de débogage à distance et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)

---
title: 'Erreur : Impossible de pas à pas automatiquement le serveur | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d75ed4ddb42705b95a5ddd834596bc828e0f3ec2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493536"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Erreur : Impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [erreur : Impossible de mettre automatiquement étape dans le serveur](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-automatically-step-into-the-server).  
  
L’erreur affiche le message suivant :  
  
 Impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur. Le débogueur n’a pas été notifié avant l’exécution de la procédure distante.  
  
 Cette erreur peut se produire lorsque vous essayez d’effectuer un pas à pas détaillé dans un service Web (consultez [Exécution pas à pas d’un service Web XML](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Elle peut survenir toute les fois que [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] n'est pas installé correctement.  
  
 Causes possibles :  
  
-   Le fichier web.config pour votre [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] application ne définit pas de débogage sur « true » (consultez [Mode débogage dans les Applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Une version de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] a été installé après l’installation de Visual Studio. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] doit être installé avant Visual Studio. Pour résoudre ce problème, dans le **Panneau de configuration**Windows, accédez à **Programmes et Fonctionnalités** afin de réparer votre installation Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Débogage à distance](../debugger/remote-debugging.md)




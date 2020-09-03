---
title: Erreur-Impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd85d5564bb6f8a0a5f4ead8c5a4ef8e1be48598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460284"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Erreur : Impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur
Le message d’erreur :

 Impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur. Le débogueur n’a pas été notifié avant l’exécution de la procédure distante.

 Cette erreur peut se produire lorsque vous essayez d’effectuer un pas à pas détaillé dans un service Web (consultez [Exécution pas à pas d’un service Web XML](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Elle peut survenir toute les fois que [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n’est pas installé correctement.

 Les causes possibles sont :

- Le fichier web.config pour votre application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n’affecte pas la valeur "true" au débogage (consultez [Mode débogage dans les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Une version de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a été installée après l’installation de Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] doit être installé avant Visual Studio. Pour résoudre ce problème, dans **Panneau de configuration Windows > Programmes et Fonctionnalités** afin de réparer votre installation Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Débogage à distance](../debugger/remote-debugging.md)
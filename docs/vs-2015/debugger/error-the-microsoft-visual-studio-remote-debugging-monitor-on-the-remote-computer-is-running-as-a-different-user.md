---
title: 'Erreur : Microsoft Visual Studio Remote Debugging Monitor sur l’ordinateur distant est en cours d’exécution en tant qu’autre utilisateur | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5256feb22e09eb75fa8f4d5a50e8beafeec8f97d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503658"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Erreur : Microsoft Visual Studio Remote Debugging Monitor sur l'ordinateur distant s'exécute avec un utilisateur différent
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [erreur : le Microsoft Visual Studio Remote Debugging Monitor sur l’ordinateur distant est en cours d’exécution en tant qu’autre utilisateur](https://docs.microsoft.com/visualstudio/debugger/error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user).  
  
Si vous essayez d'effectuer un débogage distant, vous risquez de recevoir ce message d'erreur :  
  
 Microsoft Visual Studio Remote Debugging Monitor sur l'ordinateur distant s'exécute avec un utilisateur différent.  
  
## <a name="cause"></a>Cause  
 Ce message se produit lorsque vous déboguez en mode Aucune authentification et l'utilisateur qui a démarré msvsmon n'est pas l'utilisateur qui exécute Visual Studio.  
  
## <a name="solution"></a>Solution  
 La solution la plus sûre et la mieux adaptée consiste à exécuter Remote Debugging Monitor (msvsmon.exe) sous le même compte d'utilisateur que Visual Studio. Si vous ne pouvez pas le faire, vous pouvez exécuter Remote Debugging Monitor sous l’autre compte avec le **autoriser tous les utilisateurs de déboguer** option sélectionnée dans le Remote Debugging Monitor **Options** boîte de dialogue.  
  
> [!CAUTION]
>  Accorder à d'autres utilisateurs l'autorisation de se connecter implique l'éventualité d'une connexion accidentelle à la session de débogage distant incorrecte. Débogage dans **aucune authentification** mode n’est jamais sécurisé et doit être utilisé avec précaution.  
  
 Pour plus d’informations, consultez [Démarrez Remote Debugging Monitor](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c).  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Débogage à distance](../debugger/remote-debugging.md)




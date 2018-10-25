---
title: 'Erreur : Microsoft Visual Studio Remote Debugging Monitor sur l’ordinateur distant ne dispose pas d’autorisation de se connecter à cet ordinateur | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.access_denied_oncallback
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
- remote debugging, Windows version error
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20accedd9591c777cad26aed30c05954dfabbdfc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811087"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Erreur : Microsoft Visual Studio Remote Debugging Monitor sur l'ordinateur distant ne dispose pas des autorisations pour se connecter à cet ordinateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur ce produit lorsque l'utilisateur qui tente d'exécuter Visual Studio Remote Debugging Monitor (msvsmon) ne possède pas de compte sur l'ordinateur local.  
  
### <a name="to-fix-this-problem"></a>Pour corriger ce problème  
  
- Ajoutez un compte d'utilisateur à l'ordinateur hôte du débogueur Visual Studio, en utilisant les mêmes nom et mot de passe que le compte d'utilisateur qui exécute msvsmon sur l'ordinateur distant.  
  
   \- ou -  
  
- Exécutez msvsmon en tant qu'utilisateur autorisé à appeler l'ordinateur local. Cela signifie que l'utilisateur doit être un utilisateur de domaine et un administrateur sur l'ordinateur msvsmon. Vous pouvez spécifier le compte d'utilisateur qui doit exécuter msvsmon de deux manières différentes :  
  
  - Cliquez sur l’icône msvsmon et choisissez **exécuter en tant que** dans le menu contextuel  
  
    \- ou -  
  
  - À l'invite de commandes, tapez `runas.exe`.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage distant entre des domaines](http://msdn.microsoft.com/library/8e697ce1-55e8-4ab0-a05f-f87225e2f29b)   
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)




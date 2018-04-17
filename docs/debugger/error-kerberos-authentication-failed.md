---
title: 'Erreur : Échec de l’authentification Kerberos | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec544d1d5930990dce1ca30d84a21e2e1517f0d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="error-kerberos-authentication-failed"></a>Erreur : L'authentification Kerberos a échoué
Lorsque vous essayez d'effectuer un débogage distant, le message d'erreur suivant peut s'afficher :  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.  
```  
  
 Cette erreur se produit lorsque Visual Studio Remote Debugging Monitor est exécuté sous le compte Système local ou Service réseau. Sous l'un de ces comptes, le débogueur distant doit établir une connexion d'authentification Kerberos pour communiquer avec l'ordinateur hôte du débogueur Visual Studio.  
  
 L'authentification Kerberos n'est pas disponible dans les conditions suivantes :  
  
-   L'ordinateur cible ou l'ordinateur hôte du débogueur est situé sur un groupe de travail, au lieu d'un domaine.  
  
     \- ou -  
  
-   Kerberos a été désactivé sur le contrôleur de domaine.  
  
 Si l'authentification Kerberos n'est pas disponible, modifiez le compte utilisé pour exécuter Visual Studio Remote Debugging Monitor. Pour connaître la procédure, consultez [erreur : service du débogueur distant Visual Studio sur l’ordinateur cible ne peut pas se reconnecter à cet ordinateur](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
 Si ce message s'affiche encore alors que les deux ordinateurs sont connectés au même domaine, vérifiez que le DNS sur l'ordinateur cible résout correctement le nom de l'ordinateur hôte du débogueur. Consultez la procédure suivante.  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Pour vérifier que le DNS sur l'ordinateur cible résout correctement le nom de l'ordinateur hôte du débogueur  
  
1.  Sur l’ordinateur cible, ouvrez le **Démarrer** menu, pointez sur **Accessoires** puis cliquez sur **invite de commandes**.  
  
2.  Dans le **invite de commandes** fenêtre, tapez :  
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3.  La première ligne de la réponse `ping` affiche le nom complet et l'adresse IP renvoyés par le DNS pour l'ordinateur spécifié.  
  
4.  Sur l’ordinateur hôte du débogueur, ouvrez un **invite de commandes** fenêtre et exécutez `ipconfig`.  
  
5.  Comparez les valeurs d'adresse IP.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Débogage à distance](../debugger/remote-debugging.md)
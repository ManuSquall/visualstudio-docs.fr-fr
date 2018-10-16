---
title: 'Erreur : Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) ne semble pas s’exécuter sur l’ordinateur distant | Microsoft Docs'
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
- vs.debug.error.server_machine_no_default
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 86db9931-50e3-4095-b161-802ed8ef39c9
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a706ec1f0a9fb82a02e052e81d282aef4a5a6ba
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252588"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Erreur : Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) ne semble pas s’exécuter sur l’ordinateur distant
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce message d’erreur indique que Visual Studio n’a pas pu trouver l’instance appropriée de Visual Studio Remote Debugging Monitor sur l’ordinateur distant. Visual Studio Remote Debugging Monitor doit être installé pour que le débogage distant fonctionne. Pour plus d’informations sur le téléchargement et la configuration du le débogueur distant, consultez [Set Up the Remote Tools on the Device](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
> [!IMPORTANT]
>  Si vous pensez avoir reçu ce message en raison d’un bogue présent dans le produit, veuillez signaler ce problème à Visual Studio à l’aide de la fonctionnalité [Envoyer un sourire](http://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b). Si vous avez besoin d’aide supplémentaire, consultez [Talk to Us](../ide/talk-to-us.md) pour savoir comment contacter Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>J’ai reçu ce message pendant une session de débogage dans Visual Studio 2010 ou version antérieure  
 Si vous utilisez Visual Studio 2010 ou version antérieure, vous pouvez également recevoir cette erreur si le partage de fichiers et d’imprimantes n’est pas activé. Pour en savoir plus sur ce problème, reportez-vous à la version de Visual Studio 2010 de cette documentation : [erreur : le Microsoft Visual Studio Remote Debugging Monitor (MSVSMON. (EXE) ne semble pas être en cours d’exécution sur l’ordinateur distant. -Visual Studio 2010](https://msdn.microsoft.com/library/ms164726\(v=vs.100\).aspx)  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>J’ai reçu ce message pendant une session de débogage locale  
 Si ce message s’affiche pendant un débogage local, il est possible que le problème provienne de votre antivirus ou d’un pare-feu tiers. Visual Studio étant une application 32 bits, elle utilise la version 64 bits du débogueur distant pour déboguer les applications 64 bits. Les deux processus communiquent à l’aide du réseau local au sein de l’ordinateur local. Aucun trafic ne quitte l’ordinateur, mais il peut arriver que des logiciels de sécurité tiers bloquent la communication.  
  
 Les sections suivantes répertorient les autres causes éventuelles de ce message et ce que vous pouvez faire pour résoudre le problème.  
  
## <a name="the-remote-machine-is-not-reachable"></a>L’ordinateur distant n’est pas accessible  
 Essayez d’exécuter une commande [ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) sur l’ordinateur distant. S’il ne répond pas à la commande ping, les outils à distance ne pourront pas non plus se connecter. Essayez de redémarrer l’ordinateur distant et vérifiez qu’il est correctement configuré sur le réseau.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La version du débogueur distant ne correspond pas à la version de Visual Studio  
 La version de Visual Studio que vous exécutez localement doit correspondre à la version de Remote Debugging Monitor qui s’exécute sur l’ordinateur distant. Pour résoudre ce problème, téléchargez et installez la version correspondante de Remote Debugging Monitor. Accédez au [Centre de téléchargement](http://www.microsoft.com/download) pour rechercher la version appropriée du débogueur distant.  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Les ordinateurs locaux et distants utilisent des modes d’authentification différents  
 Les ordinateurs locaux et distants doivent utiliser le même mode d’authentification. Pour résoudre ce problème, assurez-vous que les deux ordinateurs utilisent le même mode d’authentification. Pour plus d’informations sur les modes d’authentification, consultez [Vue d’ensemble de l’authentification Windows](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Le débogueur distant s’exécute sous un compte d’utilisateur différent  
 Pour résoudre ce problème, vous pouvez procéder de différentes façons :  
  
-   Vous pouvez arrêter le débogueur distant et le redémarrer avec le compte que vous utilisez sur l’ordinateur local.  
  
-   Vous pouvez démarrer le débogueur distant à partir de la ligne de commande avec le **/ allow \<nom d’utilisateur >** paramètre : `msvsmon /allow <username@computer>`  
  
-   Vous pouvez ajouter l’utilisateur aux autorisations du débogueur distant (dans la fenêtre du débogueur distant, **Outils / Autorisations**).  
  
-   Si vous ne pouvez pas utiliser les méthodes dans les étapes précédentes, vous pouvez autoriser tous les utilisateurs à effectuer un débogage distant. Dans la fenêtre du débogueur distant, accédez à la boîte de dialogue **Outils /Options** . Quand vous sélectionnez   **Aucune authentification**, vous pouvez ensuite cocher **Permettre à tous les utilisateurs de déboguer**. Toutefois, utilisez uniquement cette option si vous n’avez pas d’autre choix ou que vous êtes sur un réseau privé.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Le pare-feu sur l’ordinateur distant n’autorise pas les connexions entrantes au débogueur distant  
 Le pare-feu sur l’ordinateur Visual Studio et celui sur l’ordinateur distant doivent être configurés pour autoriser la communication entre Visual Studio et le débogueur distant. Pour plus d’informations sur les ports utilisés par le débogueur distant, consultez [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Pour plus d’informations sur la configuration du Pare-feu Windows, consultez [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Un antivirus bloque les connexions  
 L’antivirus Windows autorise les connexions au débogueur distant, mais certains antivirus tiers peuvent les bloquer. Consultez la documentation de votre antivirus pour savoir comment autoriser ces connexions.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>La stratégie de sécurité réseau bloque la communication entre l’ordinateur distant et Visual Studio  
 Passez en revue la sécurité de votre réseau pour vous assurer qu’elle ne bloque pas les communications. Pour plus d’informations sur la stratégie de sécurité réseau Windows, consultez [Gestion de la sécurité](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Le réseau est trop occupé pour prendre en charge le débogage distant  
 Dans ce cas, vous devrez peut-être procéder au débogage distant ultérieurement ou replanifier le travail sur le réseau à une heure différente.  
  
## <a name="more-help"></a>Aide supplémentaire  
 Pour obtenir de l’aide de débogueur distant, y compris les commutateurs de ligne de commande, cliquez sur **aide / utilisation** dans la fenêtre du débogueur distant. Si vous n’êtes pas ouvert, vous pouvez voir la page web en copiant la ligne suivante à une **Explorateur de fichiers** fenêtre. (Vous devrez remplacer \<répertoire d’installation de Visual Studio > avec l’emplacement de votre installation de Visual Studio.)  
  
 res : / /*\<répertoire d’installation de Visual Studio >* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs et résolution des problèmes du débogage distant](../debugger/remote-debugging-errors-and-troubleshooting.md)




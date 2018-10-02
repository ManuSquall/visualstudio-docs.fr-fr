---
title: Impossible de se connecter à Microsoft Visual Studio Remote Debugging Monitor | Microsoft Docs
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
- vs.debug.error.remote_debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edc3d1384a67576bd805ef5efb60614a215a7a92
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505976"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Impossible de se connecter à l’ordinateur Microsoft Visual Studio Remote Debugging Monitor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Impossible de se connecter à Microsoft Visual Studio Remote Debugging Monitor](https://docs.microsoft.com/visualstudio/debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor).  
  
Ce message d’erreur apparaît lorsque vous entrez un nom non valide pour Visual Studio Remote Debugging Monitor dans la boîte de dialogue **Attacher au processus** . Le nom Remote Debugging Monitor est généralement le même que celui de l’ordinateur auquel vous tentez de vous connecter pour le débogage distant. Ce message peut survenir, car l’ordinateur distant n’existe pas sur le réseau, Remote Debugging Monitor n’est pas installé correctement sur l’ordinateur distant ou l’ordinateur distant est inaccessible en raison de problèmes de réseau ou de la présence d’un pare-feu.  
  
> [!IMPORTANT]
>  Si vous pensez avoir reçu ce message en raison d’un bogue de produit, Veuillez signaler ce problème à Visual Studio [envoyer un sourire](http://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b). Si vous avez besoin d’aide supplémentaire, consultez [Talk to Us](../ide/talk-to-us.md) pour savoir comment contacter Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>J’ai reçu ce message pendant une session de débogage locale  
 Si ce message s’affiche pendant un débogage local, il est possible que le problème provienne de votre antivirus ou d’un pare-feu tiers. Visual Studio étant une application 32 bits, elle utilise la version 64 bits du débogueur distant pour déboguer les applications 64 bits. Les deux processus communiquent à l’aide du réseau local au sein de l’ordinateur local. Aucun trafic réseau ne quitte l’ordinateur, mais il peut arriver que des logiciels de sécurité tiers bloquent la communication.  
  
 Les sections suivantes répertorient les autres causes éventuelles de ce message et ce que vous pouvez faire pour résoudre le problème.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous que Visual Studio Remote Debugging Monitor est installé et exécuté sur l’ordinateur distant. Pour plus d’informations sur le débogueur distant et comment l’installer, consultez [le débogage à distance](../debugger/remote-debugging.md).  
  
-   Dans Visual Studio, examinez les propriétés du projet (**Projet/Propriétés/Débogage**). Assurez-vous que le **nom du serveur distant** est correct.  
  
-   Vérifiez que l’ordinateur distant est accessible sur le réseau.  
  
## <a name="the-remote-machine-is-not-reachable"></a>L’ordinateur distant n’est pas accessible  
 Essayez [ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) l’ordinateur distant. S’il ne répond pas à la commande ping, les outils à distance ne pourront pas non plus se connecter. Essayez de redémarrer l’ordinateur distant et vérifiez qu’il est correctement configuré sur le réseau.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La version du débogueur distant ne correspond pas à la version de Visual Studio  
 La version de Visual Studio que vous exécutez localement doit correspondre à la version de Remote Debugging Monitor qui s’exécute sur l’ordinateur distant. Pour résoudre ce problème, téléchargez et installez la version correspondante de Remote Debugging Monitor. Accédez à la [centre de téléchargement](http://www.microsoft.com/download) pour rechercher la version appropriée du débogueur distant.  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Les ordinateurs locaux et distants utilisent des modes d’authentification différents  
 Les ordinateurs locaux et distants doivent utiliser le même mode d’authentification. Pour résoudre ce problème, assurez-vous que les deux ordinateurs utilisent le même mode d’authentification. Vous pouvez modifier le mode d’authentification du débogueur distant dans la boîte de dialogue **Outils/Options** .  
  
 Pour plus d’informations sur les modes d’authentification, consultez [vue d’ensemble de l’authentification Windows](https://technet.microsoft.com/library/hh831472.aspx).  
  
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
 Passez en revue la sécurité de votre réseau pour vous assurer qu’elle ne bloque pas les communications. Pour plus d’informations sur la stratégie de sécurité réseau de Windows, consultez [gestion de la sécurité](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Le réseau est trop occupé pour prendre en charge le débogage distant  
 Dans ce cas, vous devrez peut-être procéder au débogage distant ultérieurement ou replanifier le travail sur le réseau à une heure différente.  
  
## <a name="more-help"></a>Aide supplémentaire  
 Pour obtenir de l’aide supplémentaire sur le débogueur distant, y compris sur les commutateurs de ligne de commande, ouvrez les fichiers suivants dans un navigateur :  
  
 **res://C:\Program%20Files\Microsoft%20Visual%20Studio%2014.0\Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm**  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage à distance](../debugger/remote-debugging.md)




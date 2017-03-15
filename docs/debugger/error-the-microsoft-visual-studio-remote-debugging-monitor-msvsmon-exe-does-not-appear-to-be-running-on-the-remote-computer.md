---
title: "Erreur&#160;: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) ne semble pas s’ex&#233;cuter sur l’ordinateur distant | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.server_machine_no_default"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 86db9931-50e3-4095-b161-802ed8ef39c9
caps.latest.revision: 21
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) ne semble pas s’ex&#233;cuter sur l’ordinateur distant
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce message d’erreur indique que Visual Studio n’a pas pu trouver l’instance appropriée de Visual Studio Remote Debugging Monitor sur l’ordinateur distant. Visual Studio Remote Debugging Monitor doit être installé pour que le débogage distant fonctionne. Pour plus d’informations sur le téléchargement et la configuration du le débogueur distant, consultez [Configurer les outils de contrôle à distance sur le périphérique](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
> [!IMPORTANT]
>  Si vous pensez avoir reçu ce message en raison d’un bogue présent dans le produit, veuillez signaler ce problème à Visual Studio à l’aide de la fonctionnalité [Envoyer un sourire](../Topic/Visual%20Studio%20Send%20a%20Smile%20Instructions.md). Si vous avez besoin d’aide supplémentaire, consultez [Nous contacter](../ide/talk-to-us.md) pour savoir comment contacter Microsoft.  
  
## J’ai reçu ce message pendant une session de débogage dans Visual Studio 2010 ou version antérieure  
 Si vous utilisez Visual Studio 2010 ou version antérieure, vous pouvez également recevoir cette erreur si le partage de fichiers et d’imprimantes n’est pas activé. Pour en savoir plus sur ce problème, reportez\-vous à la version de Visual Studio 2010 de cette documentation : [Erreur : Microsoft Visual Studio Remote Debugging Monitor \(MSVSMON.EXE\) ne semble pas s’exécuter sur l’ordinateur distant \- Visual Studio 2010](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx).  
  
## J’ai reçu ce message pendant une session de débogage locale  
 Si ce message s’affiche pendant un débogage local, il est possible que le problème provienne de votre antivirus ou d’un pare\-feu tiers. Visual Studio étant une application 32 bits, elle utilise la version 64 bits du débogueur distant pour déboguer les applications 64 bits. Les deux processus communiquent à l’aide du réseau local au sein de l’ordinateur local. Aucun trafic ne quitte l’ordinateur, mais il peut arriver que des logiciels de sécurité tiers bloquent la communication.  
  
 Les sections suivantes répertorient les autres causes éventuelles de ce message et ce que vous pouvez faire pour résoudre le problème.  
  
## L’ordinateur distant n’est pas accessible  
 Essayez d’exécuter une commande [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx) sur l’ordinateur distant. S’il ne répond pas à la commande ping, les outils à distance ne pourront pas non plus se connecter. Essayez de redémarrer l’ordinateur distant et vérifiez qu’il est correctement configuré sur le réseau.  
  
## La version du débogueur distant ne correspond pas à la version de Visual Studio  
 La version de Visual Studio que vous exécutez localement doit correspondre à la version de Remote Debugging Monitor qui s’exécute sur l’ordinateur distant. Pour résoudre ce problème, téléchargez et installez la version correspondante de Remote Debugging Monitor. Accédez au [Centre de téléchargement](http://www.microsoft.com/en-us/download) pour rechercher la version appropriée du débogueur distant.  
  
## Les ordinateurs locaux et distants utilisent des modes d’authentification différents  
 Les ordinateurs locaux et distants doivent utiliser le même mode d’authentification. Pour résoudre ce problème, assurez\-vous que les deux ordinateurs utilisent le même mode d’authentification. Pour plus d’informations sur les modes d’authentification, consultez [Vue d’ensemble de l’authentification Windows](https://technet.microsoft.com/en-us/library/hh831472.aspx).  
  
## Le débogueur distant s’exécute sous un compte d’utilisateur différent  
 Pour résoudre ce problème, vous pouvez procéder de différentes façons :  
  
-   Vous pouvez arrêter le débogueur distant et le redémarrer avec le compte que vous utilisez sur l’ordinateur local.  
  
-   Vous pouvez démarrer le débogueur distant à partir de la ligne de commande à l’aide du paramètre  **\/allow \<nom\_utilisateur\>** : `msvsmon /allow <username@computer>`  
  
-   Vous pouvez ajouter l’utilisateur aux autorisations du débogueur distant \(dans la fenêtre du débogueur distant, **Outils \/ Autorisations**\).  
  
-   Si vous ne pouvez pas utiliser les méthodes dans les étapes précédentes, vous pouvez autoriser tous les utilisateurs à effectuer un débogage distant. Dans la fenêtre du débogueur distant, accédez à la boîte de dialogue **Outils \/Options**. Quand vous sélectionnez **Aucune authentification**, vous pouvez ensuite cocher **Permettre à tous les utilisateurs de déboguer**. Toutefois, utilisez uniquement cette option si vous n’avez pas d’autre choix ou que vous êtes sur un réseau privé.  
  
## Le pare\-feu sur l’ordinateur distant n’autorise pas les connexions entrantes au débogueur distant  
 Le pare\-feu sur l’ordinateur Visual Studio et celui sur l’ordinateur distant doivent être configurés pour autoriser la communication entre Visual Studio et le débogueur distant. Pour plus d’informations sur les ports utilisés par le débogueur distant, consultez [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md). Pour plus d’informations sur la configuration du Pare\-feu Windows, consultez [Configurer le Pare\-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## Un antivirus bloque les connexions  
 L’antivirus Windows autorise les connexions au débogueur distant, mais certains antivirus tiers peuvent les bloquer. Consultez la documentation de votre antivirus pour savoir comment autoriser ces connexions.  
  
## La stratégie de sécurité réseau bloque la communication entre l’ordinateur distant et Visual Studio  
 Passez en revue la sécurité de votre réseau pour vous assurer qu’elle ne bloque pas les communications. Pour plus d’informations sur la stratégie de sécurité réseau Windows, consultez [Gestion de la sécurité](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## Le réseau est trop occupé pour prendre en charge le débogage distant  
 Dans ce cas, vous devrez peut\-être procéder au débogage distant ultérieurement ou replanifier le travail sur le réseau à une heure différente.  
  
## Aide supplémentaire  
 Pour obtenir de l’aide supplémentaire sur le débogueur distant, y compris sur les commutateurs de ligne de commande, ouvrez les fichiers suivants dans un navigateur :  
  
 **res:\/\/C:\\Program%20Files\\Microsoft%20Visual%20Studio%2014.0\\Common7\\IDE\\Remote%20Debugger\\x64\\msvsmon.exe\/help.htm**  
  
## Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)
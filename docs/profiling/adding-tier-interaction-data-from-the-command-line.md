---
title: "Ajout des donn&#233;es d’interaction de couche &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "profilage d’interaction de couche (méthode)"
  - "outils de profilage, méthode d’interaction de couche"
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ajout des donn&#233;es d’interaction de couche &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le profilage des interactions de couche fournit des informations supplémentaires sur les temps d'exécution des appels synchrones [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] dans les fonctions des applications multicouches qui communiquent avec une ou plusieurs bases de données.  
  
 **Windows 8 et Windows Server 2012**  
  
 Pour collecter des données sur l'interaction entre les couches sur les applications Windows 8 de bureau et Windows Server de 2012, vous devez utiliser la méthode d'instrumentation.  La collecte de données sur l'interaction entre les couches dans des applications de Windows Store n'est pas pris en charge.  
  
 **Éditions Visual Studio**  
  
 Les données de profilage d'interaction de couche peuvent être collectées à l'aide de [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], ou [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)].  Toutefois, les données de profilage d'interaction de couche peuvent être affichées uniquement dans [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] et [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
 **Collecte de données TIP sur un ordinateur distant**  
  
 Pour collecter des données sur l'interaction entre les couches sur un ordinateur distant, vous devez copier le fichier**.exe** de**vs\_profiler\_***\<Platform\>***\_***\<Language\>*du dossier de *%VSInstallDir%***\\Team Tools\\Performance Tools\\Setups** d'un ordinateur Visual Studio sur l'ordinateur distant et l'installer.  Vous ne pouvez pas utiliser les outils de profilage dans le package de téléchargement pour [Outils de contrôle à distance Visual Studio](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
 **Rapports \(TIP\)**  
  
 Les données d'interaction de couche peuvent être affichées uniquement dans l'IDE de [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].  Les rapports d'interaction de couche basés sur un fichier via [VSPerfReport](../profiling/vsperfreport.md) ne sont pas disponibles.  
  
## Ajout de données d'interaction de couche avec VSPerfCmd  
 L'outil en ligne de commande VSPerfASPNETCmd vous permet d'accéder aux fonctionnalités complètes disponibles dans les outils de profilage.  Pour ajouter une interaction de couche aux données de profilage collectées à l'aide de VSPerfCmd, vous devez utiliser l'utilitaire **VSPerfCLREnv** pour définir et supprimer les variables d'environnement qui activent les données d'interaction de couche.  Les options que vous spécifiez et les procédures obligatoires pour collecter des données dépendent du type d'application que vous profilez.  
  
### Profilage d'applications autonomes  
 Pour ajouter des données d'interaction de couche à une application qui n'est pas exécutée par un autre processus, telle qu'une application de bureau Windows qui passe des appels [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] synchrones à une base de données SQLServer, utilisez l'option **VSPerfClrEnv \/InteractionOn** pour définir les variables d'environnement et l'option **VSPerfClrEnv \/InteractionOff** pour les supprimer.  
  
 Dans l'exemple suivant, une application de bureau Windows est profilée à l'aide de la méthode d'instrumentation et les données sur l'interaction de couche sont collectées.  
  
##### Exemple de profilage d'une application de bureau Windows  
  
1.  Ouvrez une fenêtre d'invite de commandes avec des privilèges d'administrateur.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**.  Cliquez avec le bouton droit sur **Invite de commandes**, puis cliquez sur **Exécuter en tant qu'administrateur**.  
  
2.  Initialiser le profilage .NET et les variables d'environnement TIP.  Tapez la commande suivante :  
  
    ```  
    vsperfclrenv /traceon  
    vsperfclrenv /interactionon  
    ```  
  
3.  Démarrez le profileur.  Tapez la commande suivante :  
  
    ```  
    vsperfcmd /start:trace /output:Desktop_tip.vsp   
    ```  
  
4.  Démarrez l'application avec VSPerfCmd.  Tapez la commande suivante :  
  
    ```  
    vsperfcmd /launch:DesktopApp.exe  
    ```  
  
5.  Testez l'application pour collecter les données de profilage, puis fermez l'application normalement.  
  
6.  Effacez les variables d'environnement TIP.  Tapez la commande suivante :  
  
    ```  
    vsperfclrenv /off  
    ```  
  
 Pour plus d'informations, consultez [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### Profiler des services  
 Pour profiler des services, notamment des applications [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], utilisez l'option **VSPerfClrEnv \/GlobalInteractionOn** pour définir les variables d'environnement et l'option **VSPerfClrEnv \/GlobalInteractionOff** pour les supprimer.  
  
 Lorsque vous profilez des services, notamment les applications Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous devrez souvent redémarrer l'ordinateur pour activer le profilage.  
  
 Dans l'exemple suivant, un service Windows est profilé à l'aide de la méthode d'instrumentation et les données d'interaction de couche sont collectées.  
  
##### Exemple de profilage d'un service Windows  
  
1.  Si nécessaire, installez le service.  
  
2.  Ouvrez une fenêtre d'invite de commandes avec des privilèges d'administrateur.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**.  Cliquez avec le bouton droit sur **Invite de commandes**, puis cliquez sur **Exécuter en tant qu'administrateur**.  
  
3.  Initialisez les variables d'environnement de profilage .NET.  Tapez la commande suivante :  
  
    ```  
    vsperfclrenv /globaltraceon  
    ```  
  
4.  Initialisez les variables d'environnement TIP.  Tapez la commande suivante :  
  
    ```  
    vsperfclrenv /globalinteractionon  
    ```  
  
5.  Redémarrez l'ordinateur pour enregistrer les variables d'environnement.  
  
6.  Ouvrez une fenêtre d'invite de commandes avec des privilèges d'administrateur.  
  
7.  Démarrez le profileur.  Tapez la commande suivante :  
  
    ```  
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
8.  Si nécessaire, démarrez le service.  
  
9. Attachez le profileur au service.  Tapez la commande suivante :  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Testez le service et collectez les données de profilage.  
  
11. Arrêtez le profileur.  Tapez la commande suivante :  
  
     `vsperfcmd /detach`  
  
12. Désactivez les variables d'environnement de profilage .NET et TIP.  Tapez la commande suivante :  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Redémarrez l'ordinateur pour enregistrer l'effacement des variables d'environnement.  
  
 Pour plus d'informations, consultez l'une des rubriques suivantes :  
  
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
 [Profilage de services](../profiling/command-line-profiling-of-services.md)  
  
## Ajout de données d'interaction de couche avec VSPerfASPNETCmd  
 L'outil en ligne de commande VSPerfASPNETCmd vous permet de profiler facilement des applications Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Comparé à l'outil en ligne de commande **VSPerfCmd**, les options sont réduites, aucune variable d'environnement ne doit être définie et le redémarrage de l'ordinateur n'est pas obligatoire.  Ces fonctionnalités de VSPerfASPNETCmd rendent la collection de données d'interaction de couche exceptionnellement facile.  
  
 Pour ajouter l'interaction de couche aux données de profilage collectées à l'aide de VSPerfASPNETCmd, ajoutez l'option **\/TIP** à la ligne de commande.  Par exemple, utilisez la ligne de commande suivante pour collecter les données d'interaction de couche pour une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] à l'aide de la méthode d'instrumentation :  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Pour plus d'informations sur VSPerfASPNETCmd, consultez [Profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
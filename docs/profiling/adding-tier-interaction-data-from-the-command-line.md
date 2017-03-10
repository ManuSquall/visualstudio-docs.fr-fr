---
title: "Ajout des données d’interaction de couche à partir de la ligne de commande | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 6c394dfcf1c0df0cb7d006592b3dc386da328876
ms.openlocfilehash: 33bef5cc4eb777cb2778b12f919bbcac8f7cc574
ms.lasthandoff: 02/22/2017

---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Ajout des données d’interaction de couche à partir de la ligne de commande
Le profilage d’interaction de couche fournit des informations supplémentaires sur les temps d’exécution des appels [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] synchrones, contenus dans les fonctions d’applications multicouches qui communiquent avec une ou plusieurs bases de données.  
  
 **Windows 8 et Windows Server 2012**  
  
 Pour collecter des données d’interaction de couche à partir d’applications de bureau Windows 8 ou d’applications Windows Server 2012, vous devez utiliser la méthode d’instrumentation. La collecte de données d’interaction de couche à partir des applications Windows Store n’est pas prise en charge.  
  
 **Éditions Visual Studio**  
  
 Les données de profilage d’interaction de couche peuvent être collectées en utilisant [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] ou [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)]. Cependant, ces données ne peuvent être affichées que dans [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] et [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
 **Collecte de données TiP sur un ordinateur distant**  
  
 Pour collecter des données d’interaction de couche sur un ordinateur distant, vous devez copier le fichier **vs_profiler_***\<Plateforme>***_***\<Langue>***.exe** du dossier *%VSInstallDir%***\Team Tools\Performance Tools\Setups** d’un ordinateur Visual Studio vers l’ordinateur distant, puis lancer son exécution. Vous ne pouvez pas utiliser les outils de profilage contenus dans le package de téléchargement [Débogage à distance](../debugger/remote-debugging.md).  
  
 **Rapports TiP**  
  
 Les données d’interaction de couche ne peuvent être affichées que dans l’IDE [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]. Les rapports d’interaction de couche basés sur des fichiers procédant de [VSPerfReport](../profiling/vsperfreport.md) ne sont pas disponibles.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>Ajout de données d’interaction de couche avec VSPerfCmd  
 L’outil en ligne de commande VSPerfASPNETCmd permet d’accéder à l’intégralité des fonctionnalités des outils de profilage. Pour ajouter des données d’interaction de couche aux données de profilage collectées à l’aide de VSPerfCmd, utilisez l’utilitaire **VSPerfCLREnv** afin de définir et de supprimer les variables d’environnement qui activent les données d’interaction de couche. Les options que vous spécifiez et les procédures nécessaires pour collecter des données dépendent du type d’application que vous profilez.  
  
### <a name="profiling-stand-alone-applications"></a>Profilage d’applications autonomes  
 Pour ajouter des données d’interaction de couche à une application qui n’est pas exécutée par un autre processus, tel qu’une application de bureau Windows qui émet des appels [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] synchrones vers une base de données SQL Server, utilisez l’option **VSPerfClrEnv /InteractionOn** pour définir les variables d’environnement, et **VSPerfClrEnv /InteractionOff** pour les supprimer.  
  
 Dans l’exemple suivant, une application de bureau Windows est profilée à l’aide de la méthode d’instrumentation, et les données d’interaction de couche sont collectées.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Exemple de profilage d’une application de bureau Windows  
  
1.  Ouvrez une fenêtre d’invite de commande en tant qu’administrateur. Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**. Cliquez avec le bouton droit de la souris sur **Invite de commande**, puis cliquez sur **Exécuter en tant qu’administrateur**.  
  
2.  Initialisez les variables d’environnement TiP et celles du profilage .NET. Tapez les commandes suivantes :  
  
    ```  
    vsperfclrenv /traceon  
    vsperfclrenv /interactionon  
    ```  
  
3.  Démarrez le profileur. Tapez la commande suivante :  
  
    ```  
    vsperfcmd /start:trace /output:Desktop_tip.vsp   
    ```  
  
4.  Démarrez l’application avec VSPerfCmd. Tapez la commande suivante :  
  
    ```  
    vsperfcmd /launch:DesktopApp.exe  
    ```  
  
5.  Testez l’application pour collecter des données de profilage, puis fermez-la normalement.  
  
6.  Supprimez les variables d’environnement TiP. Tapez la commande suivante :  
  
    ```  
    vsperfclrenv /off  
    ```  
  
 Pour plus d’informations, consultez [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Profilage de services  
 Pour profiler des services, y compris les applications [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], utilisez l’option **VSPerfClrEnv /GlobalInteractionOn** pour définir les variables d’environnement, et **VSPerfClrEnv /GlobalInteractionOff** pour les supprimer.  
  
 Lorsque vous profilez des services, y compris les applications web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous êtes souvent amené à redémarrer l’ordinateur pour activer le profilage.  
  
 Dans l’exemple suivant, un service Windows est profilé à l’aide de la méthode d’instrumentation, et les données d’interaction de couche sont collectées.  
  
##### <a name="profiling-a-windows-service-example"></a>Exemple de profilage d’un service Windows  
  
1.  Si nécessaire, installez le service.  
  
2.  Ouvrez une fenêtre d’invite de commande en tant qu’administrateur. Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**. Cliquez avec le bouton droit de la souris sur **Invite de commande**, puis cliquez sur **Exécuter en tant qu’administrateur**.  
  
3.  Initialisez les variables d’environnement du profilage .NET. Tapez la commande suivante :  
  
    ```  
    vsperfclrenv /globaltraceon  
    ```  
  
4.  Initialisez les variables d’environnement TiP. Tapez la commande suivante :  
  
    ```  
    vsperfclrenv /globalinteractionon  
    ```  
  
5.  Redémarrez l’ordinateur pour inscrire les variables d’environnement.  
  
6.  Ouvrez une fenêtre d’invite de commande en tant qu’administrateur.  
  
7.  Démarrez le profileur. Tapez la commande suivante :  
  
    ```  
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
8.  Si nécessaire, démarrez le service.  
  
9. Attachez le profileur au service. Tapez la commande suivante :  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Testez le service, puis collectez des données de profilage.  
  
11. Arrêtez le profileur. Tapez la commande suivante :  
  
     `vsperfcmd /detach`  
  
12. Supprimez les variables d’environnement TiP et celles du profilage .NET. Tapez la commande suivante :  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Redémarrez l’ordinateur pour enregistrer la suppression des variables d’environnement.  
  
 Pour plus d'informations, consultez l'une des rubriques suivantes :  
  
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
 [Profilage de services](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>Ajout de données d’interaction de couche avec VSPerfASPNETCmd  
 L’outil en ligne de commande VSPerfASPNETCmd vous permet de profiler facilement des applications web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Par rapport à l’outil en ligne de commande **VSPerfCmd**, cet outil comporte moins d’options et ne nécessite ni configuration de variables d’environnement, ni redémarrage de l’ordinateur. Ces fonctionnalités de VSPerfASPNETCmd facilitent grandement la collecte de données d’interaction de couche.  
  
 Pour ajouter les données d’interaction de couche aux données de profilage collectées à l’aide de VSPerfASPNETCmd, ajoutez l’option **/TIP** sur la ligne de commande. Par exemple, utilisez la ligne de commande suivante pour collecter les données d’interaction de couche d’une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] à l’aide de la méthode d’instrumentation :  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Pour plus d’informations sur VSPerfASPNETCmd, consultez [Profilage de site web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

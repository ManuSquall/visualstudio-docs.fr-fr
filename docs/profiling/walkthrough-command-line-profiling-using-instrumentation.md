---
title: "Proc&#233;dure pas &#224; pas&#160;: profilage de la ligne de commande &#224; l’aide de l’instrumentation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils de profilage, procédures pas à pas"
  - "outils d’analyse des performances, procédures pas à pas"
  - "outils d’analyse des performances, outils de ligne de commande"
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Proc&#233;dure pas &#224; pas&#160;: profilage de la ligne de commande &#224; l’aide de l’instrumentation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas vous indique comment profiler une application autonome [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] pour collecter des données de temporisation détaillées et des informations sur le nombre d'appels à l'aide de la méthode d'instrumentation des outils de profilage.  Dans cette procédure pas à pas, vous effectuerez les tâches suivantes :  
  
-   Utiliser l'outil en ligne de commande [VSInstr](../profiling/vsinstr.md) pour générer des binaires instrumentés.  
  
-   Utiliser l'outil [VSPerfCLREnv](../profiling/vsperfclrenv.md) pour définir les variables d'environnement afin de collecter des données de profilage .NET.  
  
-   Utiliser l'outil [VSPerfCmd](../profiling/vsperfcmd.md) pour collecter des données de profilage.  
  
-   Utiliser l'outil [VSPerfReport](../profiling/vsperfreport.md) pour créer des rapports basés sur des fichiers des données de profilage.  
  
## Composants requis  
  
-   [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]  
  
-   Compréhension intermédiaire de C\#  
  
-   Compréhension intermédiaire de l'utilisation des outils en ligne de commande  
  
-   Une copie de [PeopleTrax, exemple](../profiling/peopletrax-sample-profiling-tools.md)  
  
-   Pour utiliser les informations fournies par le profilage, il est préférable d'avoir à disposition des informations de symboles de débogage.  Pour plus d’informations, consultez [Comment : référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
## Profilage de la ligne de commande à l'aide de la méthode d'instrumentation  
 L'instrumentation est une méthode de profilage par laquelle les versions spécialement générées des binaires profilés contiennent des fonctions de sonde qui collectent des informations de durée au niveau de l'entrée et de la sortie sur les fonctions d'un module instrumenté.  Étant donné que cette méthode de profilage est plus importante que l'échantillonnage, elle entraîne une plus grande quantité de charge mémoire.  Les binaires instrumentés sont également plus volumineux que les versions de débogage ou release et ne sont pas conçus pour le déploiement.  
  
> [!NOTE]
>  N'envoyez pas de binaires instrumentés à vos clients.  En effet, ils peuvent présenter plusieurs risques.  Ils contiennent des informations facilitant l'ingénierie à rebours de votre application et comportant donc des risques de sécurité.  
  
#### Pour profiler l'application PeopleTrax à l'aide de la méthode d'instrumentation  
  
1.  Installez l'exemple d'application PeopleTrax et générez la version Release.  
  
2.  Ouvrez une fenêtre d'invite de commandes et ajoutez le répertoire **Outils de profilage** à la variable d'environnement Path locale.  
  
3.  Remplacez le répertoire de travail par celui qui contient les binaires PeopleTrax.  
  
4.  Créez un répertoire pour contenir les rapports basés sur des fichiers.  Tapez la commande suivante :  
  
    ```  
    md Reports  
    ```  
  
5.  Utilisez l'outil en ligne de commande VSInstr pour instrumenter les binaires dans l'application.  Tapez les commandes suivantes sur des lignes de commande distinctes :  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Remarque** Par défaut, VSInstr enregistre une sauvegarde non instrumentée du fichier d'origine.  Le nom du fichier de sauvegarde a l'extension .orig.  Par exemple, la version d'origine de « MyApp.exe » serait enregistrée en tant que « MyApp.exe.orig ».  
  
6.  Tapez la commande suivante pour définir les variables d'environnement appropriées :  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  Pour démarrer le profileur, tapez la commande suivante :  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  Après avoir démarré le profileur en mode de suivi, exécutez la version instrumentée du processus PeopleTrax.exe pour collecter des données.  
  
     La fenêtre d'application **PeopleTrax** s'affiche.  
  
9. Cliquez sur **Get People**.  
  
     La grille de données PeopleTrax est remplie avec les données.  
  
10. Cliquez sur **Exporter les données**.  
  
     Le Bloc\-notes démarre et affiche un nouveau fichier qui contient une liste de personnes de l'application **PeopleTrax**.  
  
11. Fermez le Bloc\-notes, puis l'application **PeopleTrax**.  
  
12. Arrêtez le profileur.  Tapez la commande suivante :  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Tapez la commande suivante pour réinitialiser les variables d'environnement :  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Utilisez l'outil VSPerfReport pour générer des fichiers de rapports .csv \(valeurs séparées par des virgules\).  Type :  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Vous pouvez analyser les rapports générés dans un tableur ou utiliser l'IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour analyser les données de profilage dans le fichier Report.vsp.  Pour plus d’informations, consultez [Analyse des données des outils de profilage](../profiling/analyzing-performance-tools-data.md).  
  
## Voir aussi  
 [Vue d’ensemble de la session de performance](../profiling/performance-session-overview.md)   
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)   
 [Vues des rapports d’outils de profilage](../profiling/performance-report-views.md)
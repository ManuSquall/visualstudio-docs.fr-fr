---
title: "Procédure pas à pas : profilage à l’aide d’outils en ligne de commande et de l’instrumentation | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 29a68dc22a348c787d192bebecea91caed7aa0cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>Procédure pas à pas : profilage de la ligne de commande à l’aide de l’instrumentation
Cette procédure pas à pas explique comment profiler une application autonome [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] pour collecter les données de temporisation et de nombre d’appels détaillées à l’aide de la méthode d’instrumentation des outils de profilage. Dans cette procédure pas à pas, vous accomplirez les tâches suivantes :  
  
-   Utiliser l’outil en ligne de commande [VSInstr](../profiling/vsinstr.md) pour générer des binaires instrumentés  
  
-   Utiliser l’outil [VSPerfCLREnv](../profiling/vsperfclrenv.md) pour définir les variables d’environnement afin de collecter des données de profilage .NET  
  
-   Utiliser l’outil [VSPerfCmd](../profiling/vsperfcmd.md) pour collecter des données de profilage  
  
-   Utiliser l’outil [VSPerfReport](../profiling/vsperfreport.md) pour générer des rapports des données de profilage basés sur les fichiers  
  
## <a name="prerequisites"></a>Prérequis  
  
-   [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]  
  
-   Bonne connaissance de C#  
  
-   Compréhension intermédiaire de l’utilisation des outils en ligne de commande  
  
-   Une copie de l’[exemple PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md)  
  
-   Pour utiliser les informations fournies par le profilage, il est préférable de disposer des informations de symboles de débogage. Pour plus d’informations, consultez [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Profilage à l’aide d’outils en ligne de commande et de la méthode d’instrumentation  
 L’instrumentation est une méthode de profilage par laquelle des versions des binaires profilés spécialement générées contiennent des fonctions de sonde qui collectent les informations de temporisation à l’entrée et à la sortie des fonctions dans un module instrumenté. Étant donné que cette méthode de profilage est plus lourde que l’échantillonnage, elle entraîne une surcharge plus importante. En outre, les binaires instrumentés sont plus volumineux que les binaires Debug ou Release et ne sont pas destinés à être déployés.  
  
> [!NOTE]
>  N’envoyez pas de binaires instrumentés à vos clients. Les binaires instrumentés peuvent contenir plusieurs risques. Ils contiennent des informations qui facilitent l’ingénierie à rebours de votre application, ainsi que des risques pour la sécurité.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>Pour profiler l’application PeopleTrax à l’aide de la méthode d’instrumentation  
  
1.  Installez l’exemple d’application PeopleTrax et générez la version Release.  
  
2.  Ouvrez une fenêtre d’invite de commandes et ajoutez le répertoire **Outils de profilage** à la variable d’environnement Path locale.  
  
3.  Définissez le répertoire de travail sur le répertoire contenant les binaires PeopleTrax.  
  
4.  Créez un répertoire destiné à contenir les rapports basés sur les fichiers. Tapez la commande suivante :  
  
    ```  
    md Reports  
    ```  
  
5.  Utilisez l’outil en ligne de commande VSInstr pour instrumenter les binaires dans l’application. Tapez les commandes suivantes sur des lignes de commande distinctes :  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Remarque** Par défaut, VSInstr enregistre une sauvegarde non instrumentée du fichier d’origine. Le nom du fichier de sauvegarde porte l’extension .orig. Par exemple, la version d’origine de « MonApp.exe » serait enregistrée sous le nom « MonApp.exe.orig ».  
  
6.  Tapez la commande suivante pour définir les variables d’environnement appropriées :  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  Pour démarrer le profileur, tapez la commande suivante :  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  Une fois que vous avez démarré le profileur en mode trace, exécutez la version instrumentée du processus PeopleTrax.exe pour collecter des données.  
  
     La fenêtre d’application **PeopleTrax** s’affiche.  
  
9. Cliquez sur **Get People** (Obtenir des personnes).  
  
     La grille de données PeopleTrax se remplit avec des données.  
  
10. Cliquez sur **Exporter les données**.  
  
     Le Bloc-notes démarre et affiche un nouveau fichier qui contient une liste de personnes issue de l’application **PeopleTrax**.  
  
11. Fermez le Bloc-notes, puis l’application **PeopleTrax**.  
  
12. Fermez le profileur. Tapez la commande suivante :  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Tapez la commande suivante pour redéfinir les variables d’environnement :  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Utilisez l’outil VSPerfReport pour générer des fichiers de rapport de valeurs séparées par des virgules (.csv). Type :  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Vous pouvez analyser les rapports générés dans un tableur, ou vous pouvez utiliser l’IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour analyser les données de profilage dans le fichier Report.vsp. Pour plus d’informations, consultez [Analyse des données des outils d’analyse des performances](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des sessions de performances](../profiling/performance-session-overview.md)   
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)   
 [Vues du rapport des performances](../profiling/performance-report-views.md)
---
title: 'Procédure pas à pas : profilage à l’aide d’outils en ligne de commande et de l’échantillonnage | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cec9ac0038c84e267d046d35e5d65cc83d9c35c3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203214"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Procédure pas à pas : profilage de la ligne de commande à l’aide de l’échantillonnage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment profiler une application à l’aide d’outils en ligne de commande et de l’échantillonnage pour identifier les problèmes de performances.  
  
 Dans cette procédure pas à pas, vous allez voir comment profiler une application managée à l’aide d’outils de ligne de commande et utiliser l’échantillonnage pour isoler et identifier les problèmes de performances de l’application.  
  
 Dans cette procédure pas à pas, vous allez suivre les étapes suivantes :  
  
-   Profiler une application à l’aide d’outils en ligne de commande et de l’échantillonnage  
  
-   Analyser les résultats de profilage échantillonnés pour rechercher et résoudre les problèmes de performances.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]ou [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
-   Compréhension intermédiaire de [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]  
  
-   Compréhension intermédiaire de l’utilisation des outils en ligne de commande  
  
-   Une copie de l’[exemple PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md)  
  
-   Pour utiliser les informations fournies par le profilage, il est préférable de disposer des informations de symboles de débogage.  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>Profilage à l’aide d’outils en ligne de commande et de la méthode d’échantillonnage  
 L’échantillonnage est une méthode de profilage par laquelle un processus spécifique est périodiquement interrogé pour déterminer la fonction active. Les données résultantes fournissent le nombre de fois que la fonction était sur la pile des appels quand le processus a été échantillonné.  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous-répertoire \Team Tools\Performance Tools du répertoire d’installation Visual Studio. Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande. Pour plus d’informations, consultez [Spécification du chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). PeopleTrax est une application 32 bits.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Pour profiler l’application PeopleTrax à l’aide de la méthode d’échantillonnage  
  
1.  Installez l’exemple d’application PeopleTrax et générez la version Release de l’application.  
  
2.  Ouvrez une fenêtre d’invite de commandes et ajoutez le répertoire Outils de profilage à la variable d’environnement Path locale.  
  
3.  Définissez le répertoire de travail sur le répertoire contenant les binaires PeopleTrax.  
  
4.  Tapez la commande suivante pour définir les variables d’environnement appropriées :  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5.  Démarrez le profilage en exécutant VSPerfCmd.exe, outil en ligne de commande qui contrôle le profileur. La commande suivante démarre l’application et le profileur en mode d’échantillonnage :  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     Le processus du profileur démarre et s’attache au processus PeopleTrax.exe. Le processus du profileur commence à écrire les données de profilage collectées dans le fichier de rapport.  
  
6.  Cliquez sur **Get People** (Obtenir des personnes).  
  
7.  Cliquez sur **Exporter les données**.  
  
     Le Bloc-notes s’ouvre et affiche un nouveau fichier qui contient les données exportées à partir de **PeopleTrax**.  
  
8.  Fermez le Bloc-notes, puis l’application **PeopleTrax**.  
  
9. Fermez le profileur. Tapez la commande suivante :  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. Utilisez la commande suivante pour redéfinir les variables d’environnement :  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. Les données de profilage sont stockées dans le fichier.vsp. Analysez les résultats à l’aide d’une des méthodes suivantes :  
  
    -   Ouvrez le fichier.vsp dans l’IDE de Visual Studio.  
  
         — ou —  
  
    -   Générez un fichier de valeurs séparées par des virgules (.csv) à l’aide de l’outil en ligne de commande VSPerfReport.exe. Pour générer des rapports pour une utilisation en dehors de l’IDE de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], utilisez la commande suivante :  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des sessions de performances](../profiling/performance-session-overview.md)   
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)   
 [Vues du rapport des performances](../profiling/performance-report-views.md)




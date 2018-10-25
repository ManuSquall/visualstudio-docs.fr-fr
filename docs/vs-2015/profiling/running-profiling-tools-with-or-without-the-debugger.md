---
title: Exécution des outils de profilage avec ou sans le débogueur | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c190606c860a2a9d9711f0636420c34a38c8d52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813594"
---
# <a name="running-profiling-tools-with-or-without-the-debugger"></a>Exécution des outils de profilage avec ou sans le débogueur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio offre désormais une sélection d’outils d’analyse des performances. Certains d’entre eux, comme **Utilisation de l’UC** et **Utilisation de la mémoire**, peuvent être exécutés avec ou sans le débogueur. Les outils d’analyse des performances non intégrés au débogueur sont destinés à s’exécuter sur les configurations Release, tandis que ceux intégrés au débogueur sont destinés à s’exécuter sur les configurations Debug.  
  
## <a name="should-i-run-the-tool-with-or-without-the-debugger"></a>Faut-il exécuter l’outil avec ou sans le débogueur ?  
 Les outils d'analyse des performances intégrés au débogueur vous permettent d'accomplir de nombreuses tâches qui ne sont pas proposées par les outils non intégrés au débogueur, comme la définition de points d'arrêt et l'inspection des valeurs des variables. Les outils non intégrés au débogueur offrent une expérience plus proche de ce que voient les utilisateurs de l’application finale.  
  
 Voici quelques questions qui pourront vous aider à déterminer le type d'outil le mieux adapté à vos besoins :  
  
1.  Le problème a-t-il été détecté lors du développement de l’application ou dans une version finale ?  
  
     Si le problème est apparu au cours du développement, il est probablement inutile d’exécuter les outils d’analyse des performances dans une version Release. Si le problème a été décelé dans une version Release, reproduisez le problème avec une configuration Release, puis déterminez si le débogueur peut oui ou non vous aider à effectuer un examen plus approfondi.  
  
2.  Le problème est-il causé par une utilisation intensive du processeur ?  
  
     De nombreux problèmes résultent de mauvaises performances externes, comme celles liées aux opérations d'E/S sur les fichiers ou à la réactivité du réseau. Ainsi, que vous exécutiez les outils d'analyse des performances avec ou sans le débogueur, vous ne devriez pas voir beaucoup de différence. Si votre problème est dû à des appels nécessitant une utilisation importante du processeur, la différence entre les configurations Release et Debug peut être considérable. Dans ce cas, vous devrez probablement vérifier si le problème se manifeste dans la version Release avant d’utiliser les outils intégrés au débogueur.  
  
3.  Avez-vous besoin de mesurer les performances avec précision ou est-ce qu'une valeur approximative est acceptable ?  
  
     Les versions Debug ne proposent pas certaines optimisations offertes par les versions Release, comme l’incorporation des constantes et des appels de fonction, le nettoyage des chemins de code inutilisés ou encore le stockage des variables sans que celles-ci ne puissent être utilisées par le débogueur. Le débogueur lui-même affecte les performances, car il effectue certaines opérations qui sont nécessaires pour le débogage (notamment l'interception des événements d'exception et de chargement de module). Les valeurs des performances dans les outils intégrés au débogueur ont une marge de précision de l'ordre du dixième de milliseconde. Les valeurs des performances pour les configurations Release avec les outils non intégrés au débogueur sont beaucoup plus précises.  
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Collecter les données de profilage pendant le débogage  
 La section suivante porte sur le débogage local. Vous pouvez trouver des informations à propos du débogage sur un appareil, ou débogage à distance, dans les sections suivantes.  
  
1. Ouvrez le projet que vous voulez déboguer, puis cliquez sur **Déboguer/Démarrer le débogage** (ou **Démarrer** dans la barre d’outils ou **F5**).  
  
2. La fenêtre **Outils de diagnostic** apparaît automatiquement, sauf si vous l’avez désactivée. Pour réafficher la fenêtre, cliquez sur **Déboguer / Fenêtres / Afficher les outils de diagnostic**.  
  
3. Exécutez les scénarios pour lesquels vous voulez collecter des données.  
  
    Pendant l’exécution de la session, vous pouvez voir plus d’informations sur les événements, sur la mémoire du processus et sur l’utilisation de l’UC.  
  
    L’illustration suivante montre la fenêtre **Outils de diagnostic** de Visual Studio 2015 Update 1 :  
  
    ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
4. Vous pouvez choisir d’afficher **Utilisation de la mémoire** ou **Utilisation de l’UC** (ou les deux) avec le paramètre **Sélectionner les outils** sur la barre d’outils. Si vous exécutez Visual Studio Enterprise, vous pouvez activer ou désactiver IntelliTrace dans **Outils / Options / IntelliTrace**.  
  
5. La session de diagnostic se termine quand vous arrêtez le débogage.  
  
   Dans Visual Studio 2015 Update 1, la fenêtre **Outils de diagnostic** vous permet de vous concentrer sur les événements qui vous intéressent.   Les noms des événements sont désormais affichés avec les préfixes des catégories (**Mouvement**, **Sortie du programme**, **Point d’arrêt**, **Fichier,** etc.), ce qui vous permet de rechercher rapidement dans la liste une catégorie donnée ou d’ignorer les catégories qui ne vous intéressent pas.  
  
   La fenêtre a maintenant une zone de recherche permettant de rechercher une chaîne spécifique dans la liste des événements. Par exemple, l’illustration suivante montre les résultats de recherche de la chaîne « installer » pour laquelle quatre événements ont été trouvés :  
  
   ![DiagnosticsEventSearch](../profiling/media/diagnosticseventsearch.png "DiagnosticsEventSearch")  
  
   Vous pouvez également filtrer les événements de manière à les afficher ou à les masquer. Dans la liste déroulante **Filtrer** , vous pouvez activer ou désactiver des catégories spécifiques d’événements. Les noms des catégories sont les mêmes que les noms des préfixes.  
  
   ![DiagnosticEventFilter](../profiling/media/diagnosticeventfilter.png "DiagnosticEventFilter")  
  
   Pour plus d’informations, consultez [Searching and filtering the Events tab of the Diagnostic Tools window](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx).  
  
## <a name="collect-profiling-data-without-debugging"></a>Collecter les données de profilage sans débogage  
 Certains outils de profilage nécessitent des privilèges d’administrateur pour s’exécuter. Vous pouvez démarrer Visual Studio en tant qu’administrateur, ou vous pouvez choisir d’exécuter les outils en tant qu’administrateur lorsque vous démarrez la session de diagnostic.  
  
1. Ouvrez le projet dans Visual Studio.  
  
2. Dans le menu **Déboguer**, choisissez **Profileur de performances...** (Touche de raccourci : Alt+F2).  
  
3. Dans la page de lancement des outils de diagnostic, choisissez un ou plusieurs outils à exécuter dans la session. Seuls les outils applicables au type de projet, au système d'exploitation et au langage de programmation sont affichés. Lorsque vous choisissez un outil de diagnostic, les sélections d'outils qui ne peuvent pas être exécutées dans la même session de diagnostic sont désactivées. Voici comment se présenteraient vos choix pour une application universelle Windows C# :  
  
    ![Sélectionner les outils de diagnostic](../profiling/media/diag-selecttool.png "DIAG_SelectTool")  
  
4. Pour démarrer la session de diagnostic, cliquez sur **Démarrer**.  
  
5. Exécutez les scénarios pour lesquels vous souhaitez collecter des données.  
  
    Pendant l'exécution de la session, certains outils affichent des graphiques de données en temps réel dans la page de lancement des outils de diagnostic.  
  
    ![Collecter des données dans la page Performances et diagnostics](../profiling/media/pdhub-collectdata.png "PDHUB_CollectData")  
  
6. Pour terminer la session de diagnostic, cliquez sur **Arrêter la collecte**.  
  
   Lorsque vous arrêtez la collecte de données dans une session de diagnostic, les données sont analysées et le rapport s'affiche dans la page Diagnostic.  
  
   Vous pouvez également ouvrir les fichiers de session .diagnostic de la liste récemment ouverte dans la page de lancement des outils de diagnostic.  
  
   ![Ouvrir un fichier de session de diagnostic enregistré](../profiling/media/pdhub-openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
## <a name="the-profiling-report"></a>Le rapport de profilage  
 ![Rapport des outils de diagnostic](../profiling/media/diag-report.png "DIAG_Report")  
  
|||  
|-|-|  
|![Étape 1](../profiling/media/procguid-1.png "ProcGuid_1")|La chronologie indique la durée de la session de profilage, les événements d'activation du cycle de vie de l'application et les marques utilisateur.|  
|![Étape 2](../profiling/media/procguid-2.png "ProcGuid_2")|Vous pouvez limiter le rapport à une partie de la chronologie en faisant glisser les barres bleues pour sélectionner une zone de la chronologie.|  
|![Étape 3](../profiling/media/procguid-3.png "ProcGuid_3")|Un outil affiche un ou plusieurs graphiques principaux. Si votre session de diagnostic est créée avec plusieurs outils, tous les graphiques principaux sont affichés.|  
|![Étape 4](../profiling/media/procguid-4.png "ProcGuid_4")|Vous pouvez réduire ou développer les graphiques individuels.|  
|![Étape 5](../profiling/media/procguid-6.png "ProcGuid_6")|Lorsque vos données incluent les informations de plusieurs outils, les détails de l'outil sont collectés sous les onglets.|  
|![Étape 6](../profiling/media/procguid-6a.png "ProcGuid_6a")|Un outil peut avoir une ou plusieurs vues de détail. La vue est filtrée par la zone sélectionnée de la chronologie.|  
  
## <a name="setting-the-analysis-target-to-another-device"></a>Définition de la cible de l’analyse sur un autre appareil  
 Outre le démarrage de votre application à partir du projet Visual Studio, vous pouvez également exécuter les sessions de diagnostic sur d'autres cibles. Par exemple, vous pouvez souhaiter diagnostiquer les problèmes de performances sur une version de votre application installée à partir du Windows Store.  
  
 ![Choisir la cible d’analyse des outils de diagnostic](../profiling/media/pdhub-chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Vous pouvez démarrer des applications qui sont déjà installées sur un périphérique, ou vous pouvez attacher les outils de diagnostic à certaines applications qui sont déjà en cours d'exécution. Quand vous choisissez **Application en cours d’exécution** ou **Application installée**, vous sélectionnez l’application dans une liste qui identifie les applications sur la cible de déploiement spécifiée.  
  
 ![Choisir une application en cours d’exécution ou installée pour le diagnostic](../profiling/media/pdhub-selectrunningapp.png "PDHUB_SelectRunningApp")  
  
 Quand vous choisissez **Internet Explorer**, vous spécifiez l’URL et vous pouvez changer la cible de déploiement du téléphone.  
  
 ![Spécifier l’URL à afficher dans Internet Explorer](../profiling/media/pdhub-choosephoneanalysistarget.png "PDHUB_ChoosePhoneAnalysisTarget")  
  
## <a name="remote-debugging"></a>Remote Debugging  
 L’exécution d’une session de diagnostic sur un PC distant ou sur une tablette requiert que les outils de contrôle à distance Visual Studio soient installés et en cours d’exécution sur la cible distante. Pour les applications pour ordinateur, consultez [Débogage à distance](../debugger/remote-debugging.md).  Pour les applications universelles Windows, consultez [Exécuter des applications du Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
## <a name="blog-posts-and-msdn-articles-from-the-diagnostics-development-team"></a>Billets de blog et articles MSDN de l’équipe de développement Diagnostics  
 [Magazine MSDN : Analyser les performances pendant le débogage dans Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)  
  
 [Magazine MSDN : IntelliTrace permet de diagnostiquer les problèmes plus rapidement](https://msdn.microsoft.com/magazine/dn973014.aspx)  
  
 [Billet de blog : Diagnosing Event Handler Leaks with the Memory Usage Tool in Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/04/29/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015.aspx)  
  
 [Vidéo : Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)  
  
 [Vidéo : Debugging Performance Issues Using Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)  
  
 [Conseils sur les performances : Performance Information at-a-glance while Debugging with Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx)  
  
 [Diagnostic Tools debugger window in Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015.aspx)  
  
 [IntelliTrace dans Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)




---
title: À l’aide des données IntelliTrace enregistrées | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
caps.latest.revision: 112
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eef8a11f21464ea58aec8b6fb239df3ff28a40b3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950435"
---
# <a name="using-saved-intellitrace-data"></a>Utilisation des données IntelliTrace enregistrées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Accédez aux points spécifiques de l’exécution de votre application lorsque vous démarrez le débogage à partir d’un fichier journal IntelliTrace (.iTrace). Ce fichier contient des événements de performance, des exceptions, des threads, des étapes de test, des modules et d’autres informations système qu’IntelliTrace enregistre pendant que votre application s’exécute.  
  
 Vérifiez que vous disposez des éléments suivants :  
  
-   Fichiers sources et fichiers de symboles (.pdb) correspondants pour votre code d’application. Dans le cas contraire, Visual Studio ne peut pas résoudre les emplacements source et le message « Symboles introuvables » s’affiche. Consultez [spécifier le symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) et [diagnostiquer des problèmes après déploiement](../debugger/diagnose-problems-after-deployment.md).  
  
-   Visual Studio Enterprise (mais pas les éditions Professional ou Community) sur votre ordinateur de développement ou autre pour ouvrir les fichiers .iTrace  
  
-   Fichier .iTrace de l’une des sources suivantes :  
  
    |**Source**|**Consultez**|  
    |----------------|-------------|  
    |Session IntelliTrace dans Visual Studio Enterprise (mais pas dans les éditions Professional ou Community).|[Fonctionnalités IntelliTrace](../debugger/intellitrace-features.md)|  
    |Session de test dans Microsoft Test Manager. Cela lie un fichier .iTrace à un élément de travail de Team Foundation Server.|[Collecter plus de données de diagnostic dans des tests manuels](http://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
    |Microsoft Monitoring Agent, seul ou avec System Center 2012 R2 Operations Manager, pour les applications web ASP.NET et les applications SharePoint en cours d’exécution dans le déploiement|-   [Diagnostiquer des problèmes après le déploiement](../debugger/diagnose-problems-after-deployment.md)<br />-   [Nouveautés de System Center 2012 R2 Operations Manager](http://technet.microsoft.com/library/dn249700.aspx)|  
  
##  <a name="GetStarted"></a> Que voulez-vous faire ?  
  
-   [Ouvrir un fichier journal IntelliTrace](#Open)  
  
-   [Comprendre le fichier journal IntelliTrace](#Understand)  
  
-   [Démarrer le débogage à partir d’un fichier journal IntelliTrace](#StartDebugging)  
  
##  <a name="Open"></a> Ouvrir un fichier journal IntelliTrace  
 Sur un ordinateur avec Visual Studio Enterprise, ouvrez le fichier .iTrace.  
  
-   Double-cliquez sur le fichier .iTrace en dehors de Visual Studio ou ouvrez le fichier à partir de Visual Studio.  
  
     \- ou -  
  
-   Si le fichier .iTrace est attaché à un élément de travail Team Foundation Server, suivez ces étapes dans l’élément de travail :  
  
    -   Sous **Tous les liens**, recherchez le fichier .iTrace. Ouvrez-le.  
  
         \- ou -  
  
    -   Sous **Étapes de reproduction**, cliquez sur le lien **IntelliTrace** .  
  
> [!TIP]
>  Si vous avez fermé le fichier IntelliTrace pendant le débogage, vous pouvez le rouvrir facilement. Accédez au menu **Déboguer** , choisissez **IntelliTrace**, **Afficher le résumé du journal**. Vous pouvez également choisir **Afficher le résumé du journal** dans la fenêtre **IntelliTrace** . Cette commande est disponible uniquement lorsque vous procédez à un débogage à l’aide d’IntelliTrace.  
  
##  <a name="Understand"></a> Comprendre le fichier journal IntelliTrace  
 Certaines des sections suivantes du fichier .iTrace apparaissent uniquement si vous collectez les données à partir d’une source particulière, par exemple, depuis le Gestionnaire de tests ou les applications SharePoint.  
  
|**Section**|**Contient**|**Source de la collection**|  
|-----------------|------------------|---------------------------|  
|[Violations de performances](#Performance)|Événements de performance avec les appels de fonction qui dépassent le seuil configuré|Microsoft Monitoring Agent, seul ou avec System Center 2012 R2 Operations Manager pour les applications web ASP.NET hébergées sur IIS|  
|[Données d’exception](#ExceptionData)|Exceptions, notamment la pile des appels pour chaque exception|Toutes les sources|  
|[Analyse](#Analysis)|Pour les applications SharePoint 2010 et SharePoint 2013 uniquement. Diagnostiquer les événements IntelliTrace et SharePoint, tels que les événements de débogueur, les événements ULS, les exceptions non gérées et autres données que Microsoft Monitoring Agent a enregistrées.|Microsoft Monitoring Agent, seul ou avec System Center 2012 R2 Operations Manager|  
|[Informations système](#SystemInfo)|Paramètres et spécifications du système hôte|Toutes les sources|  
|[Liste de threads](#ThreadsList)|Threads exécutés pendant la collection|Toutes les sources|  
|[Données de test](#TestData)|Étapes de test et leurs résultats à partir d’une session de test|Gestionnaire de tests|  
|[Modules](#Modules)|Modules qui ciblent le processus chargé par ordre de chargement.|Toutes les sources|  
  
 Voici quelques conseils pour vous aider à retrouver les informations dans chaque section :  
  
-   Pour trier les données, choisissez un en-tête de colonne.  
  
-   Pour filtrer les données, utilisez la zone de recherche. La recherche de texte brut est effectuée dans toutes les colonnes, sauf celles de date. Vous pouvez également filtrer les recherches sur une colonne spécifique avec un filtre par colonne. Saisissez le nom de la colonne sans aucun espace, ni deux-points (**:**), et la valeur de recherche. Insérez à la suite un point-virgule (**;**) pour ajouter une autre valeur de colonne et de recherche.  
  
     Par exemple, pour rechercher les événements de performance qui ont le mot « lent » dans la colonne **Description** , tapez :  
  
     `Description:slow`  
  
##  <a name="StartDebugging"></a> Démarrer le débogage à partir d’un fichier journal IntelliTrace  
  
###  <a name="Performance"></a> Violations de performances  
 Examinez les événements de performance qui ont été enregistrés pour votre application. Vous pouvez masquer ces événements qui ne se produisent pas souvent.  
  
##### <a name="to-start-debugging-from-a-performance-event"></a>Pour démarrer le débogage à partir d’un événement de performance  
  
1.  Sous **Violations de performances**, examinez les événements de performance enregistrés, leurs durées totales d’exécution et autres informations associées. Approfondissez ensuite les méthodes appelées pendant un événement de performance spécifique.  
  
     ![Afficher les détails de l’événement performances](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     Vous pouvez aussi uniquement double-cliquer sur l’événement.  
  
2.  Dans la page d’événement, examinez les durées d’exécution de ces appels. Recherchez un appel lent dans l’arborescence d’exécution.  
  
     Les appels les plus lents s’affichent dans leur propre section lorsque vous avez plusieurs appels, imbriqués ou non.  
  
3.  Développez cet appel pour examiner les appels imbriqués et les valeurs de paramètre qui ont été enregistrés à ce moment précis.  
  
     (Clavier : Pour afficher ou masquer un appel imbriqué, appuyez sur la **flèche droite** ou **flèche gauche** respectivement de clé. Pour afficher et masquer les valeurs des paramètres d’un appel imbriqué, appuyez sur la touche **Espace** .)  
  
     Démarrez le débogage à partir de l’appel.  
  
     ![Démarrer le débogage à partir de l’appel de méthode](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     Vous pouvez également simplement double-cliquer sur l’appel ou appuyer sur la touche **Entrée** .  
  
     Si la méthode se trouve dans votre code d’application, Visual Studio y accède.  
  
     ![Accédez au code d’application à partir de l’événement de performances](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Vous pouvez maintenant examiner d’autres valeurs enregistrées, la pile des appels, parcourir votre code ou utiliser la fenêtre **IntelliTrace** pour [remonter ou avancer « dans le temps » entre d’autres méthodes](../debugger/intellitrace.md) appelées pendant cet événement de performance.  
  
###  <a name="ExceptionData"></a> Données d’exception  
 Examinez les exceptions levées et enregistrées pour votre application. Vous pouvez regrouper les exceptions qui ont le même type et la même pile des appels afin d’afficher uniquement l’exception la plus récente.  
  
##### <a name="to-start-debugging-from-an-exception"></a>Pour démarrer le débogage à partir d’une exception  
  
1.  Sous **Données d’exception**, examinez les événements d’exception enregistrés, leurs types, leurs messages et à quel moment les exceptions se sont produites. Pour approfondir le code, démarrez le débogage à partir de l’événement le plus récent d’un groupe d’exceptions.  
  
     ![Démarrer le débogage à partir de l’événement d’exception](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     Vous pouvez aussi uniquement double-cliquer sur l’événement. Si les événements ne sont pas regroupés, choisissez **Déboguer cet événement**.  
  
     Si l’exception s’est produite dans votre code d’application, Visual Studio accède à l’emplacement où l’exception s’est produite.  
  
     ![Accédez au code d’application à partir d’un événement d’exception](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Vous pouvez maintenant examiner d’autres valeurs enregistrées, la pile des appels, ou utiliser la fenêtre **IntelliTrace** pour [remonter ou avancer « dans le temps » entre les autres événements enregistrés](../debugger/intellitrace.md), le code connexe et les valeurs enregistrées à ces moments précis.  
  
    |**Colonne**|**Affiche**|  
    |----------------|-------------------|  
    |**Type**|Type .NET de l’exception|  
    |**Message le plus récent** pour les exceptions groupées ou **Message** pour les exceptions non groupées|Message fourni par l’exception|  
    |**Nombre** pour les exceptions groupées|Nombre de fois où l’exception a été levée|  
    |**ID de thread** pour les exceptions non groupées|ID du thread qui a levé l’exception|  
    |**Heure de l’événement le plus récent** ou **Heure de l’événement**|Horodatage enregistré lors de la levée de l’exception|  
    |**Pile des appels**|Pile des appels pour une exception.<br /><br /> Pour consulter la pile des appels, choisissez une exception dans la liste. La pile des appels apparaît sous la liste d’exceptions.|  
  
###  <a name="Analysis"></a> Analyse  
 Diagnostiquez les problèmes avec les applications SharePoint 2010 et SharePoint 2013 en utilisant un ID de corrélation SharePoint ou vérifiez toutes les exceptions non gérées que Microsoft Monitoring Agent a trouvées.  
  
-   Utilisez un ID de corrélation SharePoint pour rechercher ses requêtes et événements Web correspondants. Choisissez un événement, puis démarrez le débogage à l’emplacement et au moment où l’événement s’est produit.  
  
-   Si Microsoft Monitoring Agent a trouvé des exceptions non gérées, choisissez une exception, puis démarrez le débogage à l’emplacement et au moment où l’exception s’est produite.  
  
##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>Commencer à déboguer avec un ID de corrélation SharePoint  
  
1. Copiez l’ID de corrélation SharePoint à partir de sa source.  
  
    Exemple :  
  
    ![IntelliTrace &#45; erreur SharePoint &#45; ID de corrélation](../debugger/media/sharepointerror-intellitrace.png "SharePointError_IntelliTrace")  
  
2. Ouvrez le fichier .iTrace, puis pointez sur **Analyse** et entrez l’ID de corrélation SharePoint pour examiner la demande correspondante de site web et les événements inscrits.  
  
    ![Journal IntelliTrace &#45; ID de corrélation SharePoint entrez](../debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")  
  
3. Sous **Événements de requête**, examinez les événements. En commençant à partir du haut, les événements apparaissent dans l’ordre dans lequel ils se produisent.  
  
   1. Choisissez un événement pour en afficher les détails.  
  
   2. Sélectionnez **Démarrer le débogage** pour démarrer le débogage au point où l’événement s’est produit.  
  
      ![Fichier journal IntelliTrace &#45; afficher une requête web &#43; événements](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")  
  
   Vous pouvez voir ces types d’événements SharePoint avec des événements IntelliTrace :  
  
-   **Événements de profil utilisateur**  
  
     Ces événements se produisent lorsque SharePoint charge un profil utilisateur et lorsque les propriétés du profil utilisateur sont lues ou modifiées.  
  
-   **Événements ULS (Unified Logging System)**  
  
     Microsoft Monitoring Agent enregistre un sous-ensemble d’événements SharePoint ULS et de ces champs :  
  
    |**Champ IntelliTrace**|**Champ ULS SharePoint**|  
    |----------------------------|------------------------------|  
    |**Id**|**ID de l’événement**|  
    |**Niveau**|**Niveau**|  
    |**ID de catégorie**|**ID de catégorie**|  
    |**Catégorie**|**Catégorie**|  
    |**Zone**|**Produit**|  
    |**Sortie**|**Message**|  
    |**ID de corrélation**|**ID de corrélation**|  
  
##### <a name="start-debugging-from-an-unhandled-exception"></a>Démarrer le débogage à partir d’une exception non gérée  
  
1. Choisissez un ID de corrélation SharePoint pour une exception. Les exceptions sont regroupées par type et pile des appels.  
  
2. (Facultatif) Développez **Pile des appels** pour consulter la pile d’appels d’un groupe d’exceptions.  
  
3. Sélectionnez **Exception de débogage** pour démarrer le débogage à l’emplacement et au moment où l’exception s’est produite.  
  
    ![Journal IntelliTrace &#45; SharePoint des exceptions non gérées](../debugger/media/sharepointunhandledexceptions-intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")  
  
   Pour une procédure pas à pas, consultez [procédure pas à pas : Débogage d’une Application SharePoint à l’aide d’IntelliTrace](http://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4). Pour les types de données enregistrées par l’agent, consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).  
  
###  <a name="ThreadsList"></a> Liste de threads  
 Examinez les threads enregistrés qui se sont exécutés dans le processus cible. Vous pouvez commencer à déboguer à partir du premier événement IntelliTrace valide d’un thread sélectionné.  
  
##### <a name="to-start-debugging-from-a-specific-thread"></a>Pour démarrer le débogage à partir d’un thread spécifique  
  
1. Dans **Liste de threads**, choisissez un thread.  
  
2. En bas de **Liste de threads**, choisissez **Démarrer le débogage**. Vous pouvez également double-cliquer sur un thread.  
  
    Pour démarrer le débogage à partir du démarrage de l’application, double-cliquez sur **Thread principal**. Consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).  
  
   Les données de thread créées par l’utilisateur peuvent être plus utiles que les threads qu’un serveur crée et gère pour les applications web hébergées par IIS.  
  
|**Colonne**|**Affiche**|  
|----------------|-------------------|  
|**ID**|Numéro d’ID de thread|  
|**Name**|Nom du thread. Les threads sans nom apparaissent en tant que « \<Sans nom> ».|  
|**Heure de début**|Heure de création du thread.|  
|**Heure de fin**|Heure à laquelle le thread s’est terminé|  
  
###  <a name="TestData"></a> Données de test  
 Examinez les données IntelliTrace que le Gestionnaire de tests a enregistrées pendant le test de votre application.  
  
##### <a name="to-start-debugging-from-a-specific-test-step"></a>Pour démarrer le débogage à partir d’une étape de test spécifique  
  
1.  Développez **Grille d’étapes de test**. Sélectionnez une étape de test.  
  
2.  Au bas de **Grille d’étapes de test**, sélectionnez **Démarrer le débogage**. Vous pouvez également double-cliquer sur une étape de test.  
  
     Cette action démarre le débogage à partir du premier événement IntelliTrace valide après l’étape de test sélectionnée.  
  
     Si les données de test existent, IntelliTrace tente de résoudre la build Team Foundation Server associée, utilisée pour effectuer l’exécution du test. Si la build est trouvée, les symboles associés pour l’application sont résolus automatiquement.  
  
|**Champ**|**Affiche**|  
|---------------|-------------------|  
|**Session de test**|Sessions de test enregistrées. En général, il n’en existe qu’une. Cette liste est vide si les données de test ont été créées à l’aide d’un test exploratoire manuel.|  
|**Cas de test**|Cas de test à partir de la session de test sélectionnée. Cette liste est vide si les données de test ont été créées à l’aide d’un test exploratoire manuel.|  
|**Grille d’étapes de test**|Étapes de test enregistrées dont le résultat de test est Réussite ou Échec|  
  
###  <a name="SystemInfo"></a> Informations système  
 Cette section vous montre les détails sur le système qui a hébergé l’application : par exemple, le matériel, le système d’exploitation et les informations relatives à l’environnement ou spécifiques au processus.  
  
###  <a name="Modules"></a> Modules  
 Cette section montre les modules chargés par le processus cible. Les modules apparaissent par ordre de chargement.  
  
|**Colonne**|**Affiche**|  
|----------------|-------------------|  
|**Nom du module**|Nom de fichier du module|  
|**Chemin du module**|Emplacement de chargement du module sur le disque|  
|**ID de module**|Identificateur unique du module, spécifique à la version et qui contribue aux fichiers de symboles correspondants (PDB). Consultez [Finding symbol (.pdb) files and source files](http://msdn.microsoft.com/05384c85-d264-4e18-abaa-aa482ab25470).|  
  
### <a name="where-can-i-get-more-information"></a>Où peut-on obtenir plus d’informations ?  
 [Utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
 [Fonctionnalités IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Collecter plus de données de diagnostic dans des tests manuels](http://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)  
  
 [IntelliTrace](../debugger/intellitrace.md)  
  
#### <a name="forums"></a>Forums  
 [Débogueur Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
#### <a name="guidance"></a>Conseils  
 [Test de livraison continue avec Visual Studio 2012 – chapitre 6 : Une boîte à outils de test](http://go.microsoft.com/fwlink/?LinkID=255203)

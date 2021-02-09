---
title: Utilisation des données IntelliTrace enregistrées | Microsoft Docs
description: Utilisez un fichier IntelliTrace (. iTrace) pour démarrer le débogage à un point d’exécution spécifique. Le fichier contient des informations qu’IntelliTrace a enregistrées à partir d’une exécution de votre application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c81020b7c1933075f2faee026be17dd0fec4319
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884440"
---
# <a name="using-saved-intellitrace-data-c-visual-basic-c"></a>Utilisation des données IntelliTrace enregistrées (C#, Visual Basic, C++)

Accédez aux points spécifiques de l’exécution de votre application lorsque vous démarrez le débogage à partir d’un fichier journal IntelliTrace (.iTrace). Ce fichier contient des événements de performance, des exceptions, des threads, des étapes de test, des modules et d’autres informations système qu’IntelliTrace enregistre pendant que votre application s’exécute.

 Vérifiez que vous avez effectué ces actions :

- Fichiers sources et fichiers de symboles (.pdb) correspondants pour votre code d’application. Dans le cas contraire, Visual Studio ne peut pas résoudre les emplacements source et le message « Symboles introuvables » s’affiche. Consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) et [diagnostiquer les problèmes après le déploiement](../debugger/diagnose-problems-after-deployment.md).

- Visual Studio Enterprise (mais pas les éditions Professional ou Community) sur votre ordinateur de développement ou autre pour ouvrir les fichiers .iTrace

- Fichier .iTrace de l’une des sources suivantes :

    |**Source**|**Verr**|
    |----------------|-------------|
    |Session IntelliTrace dans Visual Studio Enterprise (mais pas dans les éditions Professional ou Community).|[Fonctionnalités IntelliTrace](../debugger/intellitrace-features.md)|
    |Microsoft Monitoring Agent, seul ou avec System Center 2012 R2 Operations Manager, pour les applications web ASP.NET et les applications SharePoint en cours d’exécution dans le déploiement|-   [Diagnostiquer les problèmes après le déploiement](../debugger/diagnose-problems-after-deployment.md)<br />-   [Nouveautés de System Center 2012 R2 Operations Manager](/previous-versions/system-center/system-center-2012-R2/dn249700(v=sc.12))|

## <a name="what-do-you-want-to-do"></a><a name="GetStarted"></a> Tu veux faire quoi?

- [Ouvrir un fichier journal IntelliTrace](#Open)

- [Comprendre le fichier journal IntelliTrace](#Understand)

- [Démarrer le débogage à partir d’un fichier journal IntelliTrace](#StartDebugging)

## <a name="open-an-intellitrace-log"></a><a name="Open"></a> Ouvrir un Journal IntelliTrace
 Sur un ordinateur avec Visual Studio Enterprise, ouvrez le fichier .iTrace.

- Double-cliquez sur le fichier .iTrace en dehors de Visual Studio ou ouvrez le fichier à partir de Visual Studio.

     \- ou -

- Si le fichier .iTrace est attaché à un élément de travail Team Foundation Server, suivez ces étapes dans l’élément de travail :

  - Sous **Tous les liens**, recherchez le fichier .iTrace. Ouvrez-le.

    \- ou -

  - Sous **Étapes de reproduction**, cliquez sur le lien **IntelliTrace** .

> [!TIP]
> Si vous avez fermé le fichier IntelliTrace pendant le débogage, vous pouvez le rouvrir facilement. Accédez au menu **Déboguer** , choisissez **IntelliTrace**, **Afficher le résumé du journal**. Vous pouvez également choisir **Afficher le résumé du journal** dans la fenêtre **IntelliTrace** . Cette commande est disponible uniquement lorsque vous procédez à un débogage à l’aide d’IntelliTrace.

## <a name="understand-the-intellitrace-log"></a><a name="Understand"></a> Comprendre le Journal IntelliTrace
 Certaines des sections suivantes du fichier. iTrace apparaissent uniquement si vous avez collecté des données à partir d’une source particulière, par exemple, à partir d’applications SharePoint.

|**Section**|**Contains**|**Source de la collection**|
|-----------------|------------------|---------------------------|
|[Violations de performances](#Performance)|Événements de performance avec les appels de fonction qui dépassent le seuil configuré|Microsoft Monitoring Agent, un collecteur autonome ou un Operations Manager System Center 2012 R2 pour les applications Web ASP.NET hébergées sur IIS|
|[Données d’exception](#ExceptionData)|Exceptions, notamment la pile des appels pour chaque exception|Toutes les sources|
|[Analyse](#Analysis)|Pour les applications SharePoint 2010 et SharePoint 2013 uniquement. Diagnostiquer les événements IntelliTrace et SharePoint, tels que les événements de débogueur, les événements ULS, les exceptions non gérées et autres données que Microsoft Monitoring Agent a enregistrées.|Microsoft Monitoring Agent, un collecteur autonome ou avec System Center 2012 R2 Operations Manager|
|[Informations système](#SystemInfo)|Paramètres et spécifications du système hôte|Toutes les sources|
|[Liste de threads](#ThreadsList)|Threads exécutés pendant la collection|Toutes les sources|
|[Modules](#Modules)|Modules qui ciblent le processus chargé par ordre de chargement.|Toutes les sources|
|[Web Request](#Modules)|Données de requête Web pour les applications Web IIS de production et SharePoint 2010 et SharePoint 2013|Microsoft Monitoring Agent et le collecteur autonome|

 Voici quelques conseils pour vous aider à retrouver les informations dans chaque section :

- Pour trier les données, choisissez un en-tête de colonne.

- Pour filtrer les données, utilisez la zone de recherche. La recherche de texte brut est effectuée dans toutes les colonnes, sauf celles de date. Vous pouvez également filtrer les recherches sur une colonne spécifique avec un filtre par colonne. Saisissez le nom de la colonne sans aucun espace, ni deux-points (**:**), et la valeur de recherche. Insérez à la suite un point-virgule (**;**) pour ajouter une autre valeur de colonne et de recherche.

     Par exemple, pour rechercher les événements de performance qui ont le mot « lent » dans la colonne **Description** , tapez :

     `Description:slow`

## <a name="start-debugging-from-an-intellitrace-log"></a><a name="StartDebugging"></a> Démarrer le débogage à partir d’un Journal IntelliTrace

### <a name="performance-violations"></a><a name="Performance"></a> Violations de performances
 Examinez les événements de performance qui ont été enregistrés pour votre application. Vous pouvez masquer ces événements qui ne se produisent pas souvent.

##### <a name="to-start-debugging-from-a-performance-event"></a>Pour démarrer le débogage à partir d’un événement de performance

1. Sous **Violations de performances**, examinez les événements de performance enregistrés, leurs durées totales d’exécution et les autres informations associées. Approfondissez ensuite les méthodes appelées pendant un événement de performance spécifique.

     ![Afficher les détails de l'événement de performance](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     Vous pouvez aussi uniquement double-cliquer sur l’événement.

2. Dans la page d’événement, examinez les durées d’exécution de ces appels. Recherchez un appel lent dans l’arborescence d’exécution.

     Les appels les plus lents s’affichent dans leur propre section quand vous avez plusieurs appels, imbriqués ou non.

3. Développez cet appel pour examiner les appels imbriqués et les valeurs de paramètre qui ont été enregistrés à ce moment précis.

     (Clavier : pour afficher ou masquer un appel imbriqué, appuyez respectivement sur la touche **Flèche droite** ou **Flèche gauche** . Pour afficher et masquer les valeurs des paramètres d’un appel imbriqué, appuyez sur la touche **Espace** .)

     Démarrez le débogage à partir de l’appel.

     ![Démarrer le débogage à partir d'un appel de méthode](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     Vous pouvez également simplement double-cliquer sur l’appel ou appuyer sur la touche **Entrée** .

     Si la méthode se trouve dans votre code d’application, Visual Studio y accède.

     ![Accéder au code de l'application à partir d'un événement de performance](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     Vous pouvez maintenant examiner d’autres valeurs enregistrées, la pile des appels, parcourir votre code ou utiliser la fenêtre **IntelliTrace** pour [remonter ou avancer « dans le temps » entre d’autres méthodes](../debugger/intellitrace.md) appelées pendant cet événement de performance.

### <a name="exception-data"></a><a name="ExceptionData"></a> Données d’exception
 Examinez les exceptions levées et enregistrées pour votre application. Vous pouvez regrouper les exceptions qui ont le même type et la même pile des appels afin d’afficher uniquement l’exception la plus récente.

##### <a name="to-start-debugging-from-an-exception"></a>Pour démarrer le débogage à partir d’une exception

1. Sous **Données d’exception**, examinez les événements d’exception enregistrés, leurs types, leurs messages et à quel moment les exceptions se sont produites. Pour approfondir le code, démarrez le débogage à partir de l’événement le plus récent d’un groupe d’exceptions.

     ![Commencer le débogage à partir d'un événement d'exception](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     Vous pouvez aussi uniquement double-cliquer sur l’événement. Si les événements ne sont pas regroupés, choisissez **Déboguer cet événement**.

     Si l’exception s’est produite dans votre code d’application, Visual Studio accède à l’emplacement où l’exception s’est produite.

     ![Accéder au code de l'application à partir d'un événement d'exception](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     Vous pouvez maintenant examiner d’autres valeurs enregistrées, la pile des appels, ou utiliser la fenêtre **IntelliTrace** pour [remonter ou avancer « dans le temps » entre les autres événements enregistrés](../debugger/intellitrace.md), le code connexe et les valeurs enregistrées à ces moments précis.

    |**Colonne**|**Affiche**|
    |----------------|-------------------|
    |**Type**|Type .NET de l’exception|
    |**Message le plus récent** pour les exceptions groupées ou **Message** pour les exceptions non groupées|Message fourni par l’exception|
    |**Nombre** pour les exceptions groupées|Nombre de fois où l’exception a été levée|
    |**ID de thread** pour les exceptions non groupées|ID du thread qui a levé l’exception|
    |**Heure de l’événement le plus récent** ou **Heure de l’événement**|Horodatage enregistré lors de la levée de l’exception|
    |**Pile des appels**|Pile des appels pour une exception.<br /><br /> Pour consulter la pile des appels, choisissez une exception dans la liste. La pile des appels apparaît sous la liste d’exceptions.|

### <a name="analysis"></a><a name="Analysis"></a> Analysis
 Diagnostiquez les problèmes avec les applications SharePoint 2010 et SharePoint 2013 en utilisant un ID de corrélation SharePoint ou vérifiez toutes les exceptions non gérées que Microsoft Monitoring Agent a trouvées.

- Utilisez un ID de corrélation SharePoint pour rechercher ses requêtes et événements Web correspondants. Choisissez un événement, puis démarrez le débogage à l’emplacement et au moment où l’événement s’est produit.

- Si Microsoft Monitoring Agent a trouvé des exceptions non gérées, choisissez une exception, puis démarrez le débogage à l’emplacement et au moment où l’exception s’est produite.

##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>Commencer à déboguer avec un ID de corrélation SharePoint

1. Copiez l’ID de corrélation SharePoint à partir de sa source.

    Par exemple :

    ![&#45; d’IntelliTrace &#45; d’erreur SharePoint ID de corrélation](../debugger/media/sharepointerror_intellitrace.png "SharePointError_IntelliTrace")

2. Ouvrez le fichier .iTrace, puis pointez sur **Analyse** et entrez l’ID de corrélation SharePoint pour examiner la demande correspondante de site web et les événements inscrits.

    ![Journal IntelliTrace &#45; entrer l’ID de corrélation SharePoint](../debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")

3. Sous **Événements de requête**, examinez les événements. En commençant à partir du haut, les événements apparaissent dans l’ordre dans lequel ils se produisent.

   1. Choisissez un événement pour en afficher les détails.

   2. Sélectionnez **Démarrer le débogage** pour démarrer le débogage au point où l’événement s’est produit.

      ![Fichier Journal IntelliTrace &#45; afficher les événements de la requête Web &#43;](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")

   Vous pouvez voir ces types d’événements SharePoint avec des événements IntelliTrace :

- **Événements de profil utilisateur**

     Ces événements se produisent lorsque SharePoint charge un profil utilisateur et lorsque les propriétés du profil utilisateur sont lues ou modifiées.

- **Événements ULS (Unified Logging System)**

     Microsoft Monitoring Agent enregistre un sous-ensemble d’événements SharePoint ULS et de ces champs :

    |**Champ IntelliTrace**|**Champ ULS SharePoint**|
    |----------------------------|------------------------------|
    |**Identifiant**|**EventID**|
    |**Niveau**|**Niveau**|
    |**ID de la catégorie**|**ID de la catégorie**|
    |**Catégorie**|**Catégorie**|
    |**Zone**|**Produit**|
    |**Sortie**|**Message**|
    |**ID de corrélation :**|**ID de corrélation :**|

##### <a name="start-debugging-from-an-unhandled-exception"></a>Démarrer le débogage à partir d’une exception non gérée

1. Choisissez un ID de corrélation SharePoint pour une exception. Les exceptions sont regroupées par type et pile des appels.

2. (Facultatif) Développez **Pile des appels** pour consulter la pile d’appels d’un groupe d’exceptions.

3. Sélectionnez **Exception de débogage** pour démarrer le débogage à l’emplacement et au moment où l’exception s’est produite.

    ![Journal IntelliTrace &#45; exceptions non gérées SharePoint](../debugger/media/sharepointunhandledexceptions_intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")

   Pour obtenir une procédure pas à pas, consultez [procédure pas à pas : débogage d’une application SharePoint à l’aide d’IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md). Pour obtenir les types de données que l’agent enregistre, consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).

### <a name="threads-list"></a><a name="ThreadsList"></a> Liste des threads
 Examinez les threads enregistrés qui se sont exécutés dans le processus cible. Vous pouvez commencer à déboguer à partir du premier événement IntelliTrace valide d’un thread sélectionné.

##### <a name="to-start-debugging-from-a-specific-thread"></a>Pour démarrer le débogage à partir d’un thread spécifique

1. Dans **Liste de threads**, choisissez un thread.

2. En bas de **Liste de threads**, choisissez **Démarrer le débogage**. Vous pouvez également double-cliquer sur un thread.

    Pour démarrer le débogage à partir du démarrage de l’application, double-cliquez sur **Thread principal**. Consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).

   Les données de thread créées par l’utilisateur peuvent être plus utiles que les threads qu’un serveur crée et gère pour les applications web hébergées par IIS.

|**Colonne**|**Affiche**|
|----------------|-------------------|
|**Identifiant**|Numéro d’ID de thread|
|**Nom**|Nom du thread. Les threads sans nom apparaissent en tant que « \<No Name> ».|
|**Start Time**|Heure de création du thread.|
|**Heure de fin**|Heure à laquelle le thread s’est terminé|

##### <a name="to-start-debugging-from-a-specific-test-step"></a>Pour démarrer le débogage à partir d’une étape de test spécifique

1. Développez **Grille d’étapes de test**. Sélectionnez une étape de test.

2. Au bas de **Grille d’étapes de test**, sélectionnez **Démarrer le débogage**. Vous pouvez également double-cliquer sur une étape de test.

     Cette action démarre le débogage à partir du premier événement IntelliTrace valide après l’étape de test sélectionnée.

     Si les données de test existent, IntelliTrace tente de résoudre la build Team Foundation Server associée, utilisée pour effectuer l’exécution du test. Si la build est trouvée, les symboles associés pour l’application sont résolus automatiquement.

|**Champ**|**Affiche**|
|---------------|-------------------|
|**Session de test**|Sessions de test enregistrées. En général, il n’en existe qu’une. Cette liste est vide si les données de test ont été créées à l’aide d’un test exploratoire manuel.|
|**Cas de test**|Cas de test à partir de la session de test sélectionnée. Cette liste est vide si les données de test ont été créées à l’aide d’un test exploratoire manuel.|
|**Grille d’étapes de test**|Étapes de test enregistrées dont le résultat de test est Réussite ou Échec|

### <a name="system-info"></a><a name="SystemInfo"></a> Informations système
 Cette section vous montre les détails sur le système qui a hébergé l’application : par exemple, le matériel, le système d’exploitation et les informations relatives à l’environnement ou spécifiques au processus.

### <a name="modules"></a><a name="Modules"></a> Actualis
 Cette section montre les modules chargés par le processus cible. Les modules apparaissent par ordre de chargement.

|**Colonne**|**Affiche**|
|----------------|-------------------|
|**Nom du module**|Nom de fichier du module|
|**Chemin du module**|Emplacement de chargement du module sur le disque|
|**ID de module**|Identificateur unique du module, spécifique à la version et qui contribue aux fichiers de symboles correspondants (PDB). Consultez [Finding symbol (.pdb) files and source files](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).|

### <a name="where-can-i-get-more-information"></a>Où puis-je obtenir plus d'informations ?
 [Utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

 [Fonctionnalités IntelliTrace](../debugger/intellitrace-features.md)

 [Collecter plus de données de diagnostic dans des tests manuels](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)

 [IntelliTrace](../debugger/intellitrace.md)

#### <a name="forums"></a>Forums
 [Débogueur Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)

#### <a name="guidance"></a>Guidance
 [Test de la livraison continue avec Visual Studio 2012-chapitre 6 : boîte à outils de test](/previous-versions/msp-n-p/jj159337(v=pandp.10))

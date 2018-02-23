---
title: IntelliTrace | Documents Microsoft
ms.custom: 
ms.date: 07/18/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 07afad8b464e266477c4edbb97ffc3eb3d8436e4
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="intellitrace"></a>IntelliTrace

Vous pouvez consacrer moins de temps au débogage de votre application quand vous utilisez IntelliTrace pour enregistrer et effectuer le suivi de l'historique d'exécution de votre code. Vous pouvez trouver des bogues facilement car IntelliTrace vous permet d'effectuer les tâches suivantes :

- enregistrer des événements spécifiques ;

     Examiner le code connexe, les données qui apparaissent dans le **variables locales** fenêtre pendant les événements de débogueur et les informations sur les appels de fonction

- déboguer les erreurs qu'il est difficile de reproduire ou qui interviennent lors du déploiement.

Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise Edition (mais pas dans les éditions Professional ou Community).

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

|||
|-|-|
|**Déboguer mon application avec IntelliTrace :**<br /><br /> -Afficher les événements passés.<br />-Afficher les événements passés à des informations d’appel.<br />-Enregistrer ma session IntelliTrace.<br />-Contrôle les données collectées par IntelliTrace.|- [Procédure pas à pas : Utilisation d’IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [Fonctionnalités d’IntelliTrace](../debugger/intellitrace-features.md)<br />- [Débogage d’historique](../debugger/historical-debugging.md)<br />- [Afficher des instantanés à l’aide d’IntelliTrace étape différée](../debugger/how-to-use-intellitrace-step-back.md)|
|**Collecter les données IntelliTrace pendant une session de test dans Test Manager**|- [Collecter les données de diagnostic plus dans les tests manuels](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)|
|**Collecter des données IntelliTrace à partir des applications déployées**|- [Utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Démarrez le débogage à partir d’un fichier de journal IntelliTrace (fichier .iTrace).**|- [À l’aide des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md)|

## <a name="IntelliTraceSupport"></a> Quelles applications puis-je déboguer avec IntelliTrace ?

|||
|-|-|
|**Prise en charge**|-Applications Visual Basic et Visual c# qui utilisent .NET Framework 2.0 ou versions ultérieures.<br/>Vous pouvez déboguer la plupart des applications, notamment ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010 et SharePoint 2013, ainsi que les applications 64 bits.<br/>Pour déboguer des applications SharePoint avec IntelliTrace, consultez [procédure pas à pas : débogage d’une Application SharePoint à l’aide de IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Pour déboguer des applications Microsoft Azure avec IntelliTrace, consultez [débogage d’un Service Cloud publié avec IntelliTrace et Visual Studio](/azure/vs-azure-tools-intellitrace-debug-published-cloud-services).|
|**Prise en charge limitée**|-.NET core et des applications ASP.NET Core pris en charge pour les événements uniquement<br />-Applications F # à titre expérimental<br />-Les applications UWP prise en charge pour les événements uniquement|
|Non pris en charge|-C++, autres langages et script<br />-Services Windows, Silverlight, Xbox ou [!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)] applications|

> [!NOTE]
> Si vous souhaitez déboguer un processus est déjà en cours d’exécution, vous pouvez collecter des événements IntelliTrace uniquement (aucune information d’appel). Vous pouvez attacher à un processus 32 bits ou 64 bits sur l’ordinateur local uniquement. Les événements qui se produisent avant d’attacher au processus ne sont pas collectés.

##  <a name="IntelliTraceVSTraditional"></a> Pourquoi déboguer avec IntelliTrace ?

Traditionnel ou *live* débogage affiche uniquement de votre application à l’état actuel, avec des données limitées sur les événements passés. Vous devez déduire ces événements en fonction de l'état actuel de l'application ou recréer ces événements en réexécutant votre application.

IntelliTrace développe cette expérience de débogage traditionnel en enregistrant les événements et les données spécifiques à ces instants donnés dans le temps. Cela vous permet de voir ce qui s'est produit dans votre application sans la redémarrer, surtout si vous avez dépassé l'emplacement où se trouve le bogue. IntelliTrace est activé par défaut pendant un débogage traditionnel et collecte les données automatiquement et de façon invisible. Cela vous permet de basculer facilement entre le débogage traditionnel et le débogage IntelliTrace pour consulter les informations enregistrées. Consultez [des fonctionnalités IntelliTrace](../debugger/intellitrace-features.md) et [les données collectées ?](#WhatData)

IntelliTrace peut également vous aider à déboguer des erreurs difficiles à reproduire ou celles qui se produisent lors du déploiement. Vous pouvez collecter les données IntelliTrace et les enregistrer dans un fichier journal IntelliTrace (fichier .iTrace). Un fichier .iTrace contient des informations détaillées sur les exceptions, les événements de performance, les requêtes web, les données de test, les threads, les modules et autres informations système. Vous pouvez ouvrir ce fichier dans Visual Studio Ultimate, sélectionner un élément et démarrer le débogage avec IntelliTrace. Cela vous permet d'accéder à n'importe quel événement dans le fichier et de consulter les détails spécifiques relatifs à votre application à ce moment-là.

Vous pouvez enregistrer les données IntelliTrace à partir des sources suivantes :

- Session IntelliTrace dans les versions précédentes de Visual Studio Ultimate, Visual Studio 2015 Enterprise ou Visual Studio 2017 Enterprise.

- Une session de test dans Microsoft Test Manager.

- Applications Web ASP.NET hébergées sur IIS, ou applications SharePoint 2010 et SharePoint 2013 qui s'exécutent dans le déploiement lorsque vous utilisez Microsoft Monitoring Agent, seul ou conjointement à System Center 2012. Consultez [utiliser le collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) et [analyse avec Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).

 Voici quelques exemples pour vous aider à effectuer un débogage avec IntelliTrace :

- Votre application a endommagé un fichier de données, mais vous ignorez à quel emplacement cet événement s'est produit.

     Sans IntelliTrace, vous devez parcourir le code pour rechercher tous les accès possibles au fichier, placer des points d'arrêt sur ces accès, puis réexécuter votre application pour identifier l'emplacement où le problème s'est produit. Grâce à IntelliTrace, vous pouvez consulter tous les événements d'accès au fichier et des détails spécifiques relatifs à votre application quand chaque événement s'est produit.

- Une exception se produit.

     Sans IntelliTrace, vous recevez un message concernant une exception, mais vous n’avez plus d’informations sur les événements qui a provoqué l’exception. Vous pouvez examiner la pile des appels pour consulter la chaîne d’appels qui a provoqué l’exception, mais vous ne voyez pas la séquence d’événements qui se sont produits pendant ces appels. Grâce à IntelliTrace, vous pouvez examiner les événements antérieurs à l'exception.

- Votre application se bloque sur un ordinateur de test, mais s'exécute correctement sur un ordinateur de développement.

     Vous pouvez collecter les données IntelliTrace avec Microsoft Test Manager, enregistrer les données dans un fichier .iTrace et attacher ce fichier à un élément de travail Team Foundation Server pour un examen approfondi. Consultez [collecter des données de diagnostic plus dans les tests manuels](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests) et [utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md).

- Un bogue ou un incident se produit dans une application déployée.

     Pour les applications basées sur Microsoft Azure, vous pouvez configurer la collecte de données IntelliTrace avant de publier l'application. Pendant que votre application s'exécute, IntelliTrace enregistre les données dans un fichier .iTrace. Consultez [déboguer un Service Cloud publié avec IntelliTrace et Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).

     Pour les applications web ASP.NET hébergées sur IIS 7.0, 7.5 et 8.0, et les applications SharePoint 2010 ou SharePoint 2013, utilisez Microsoft Monitoring Agent, seul ou avec System Center 2012, pour enregistrer les données IntelliTrace dans un fichier .iTrace.

     Cela est utile lorsque vous souhaitez diagnostiquer les problèmes liés aux applications du déploiement. Consultez [utiliser le collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

##  <a name="WhatData"></a> Quelles sont les données collectées par IntelliTrace ?

**Collecter des informations sur les événements**

Par défaut, IntelliTrace enregistre uniquement les événements IntelliTrace : événements de débogueur, exceptions, événements .NET Framework et autres événements système qui peuvent vous aider lors d’un débogage. Déterminez le type d’événements IntelliTrace à collecter, à l’exception des événements et des exceptions du débogueur, qui sont collectés systématiquement. Consultez [des fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).

- **Événements de débogueur**

     IntelliTrace enregistre systématiquement les événements intervenus dans le débogueur Visual Studio. Par exemple, le démarrage de votre application est un événement du débogueur. Les autres événements du débogueur sont les événements d'arrêt, qui interrompent l'exécution de votre application. Par exemple, votre programme atteint un point d’arrêt, un point de trace ou s’il exécute une **étape** commande.

     Par défaut, pour améliorer les performances, IntelliTrace n’enregistre pas toutes les valeurs possibles pour un événement du débogueur. En revanche, il enregistre les valeurs suivantes :

    - Les valeurs dans le **variables locales** fenêtre. Conserver le **variables locales** fenêtre ouverte pour afficher ces valeurs.

    - Les valeurs dans le **automatique** fenêtre uniquement lorsque le **automatique** fenêtre est ouverte

    - Valeurs situées dans DataTips qui apparaissent lorsque vous déplacez le pointeur de la souris au-dessus d'une variable dans la fenêtre source pour afficher sa valeur. IntelliTrace ne collecte pas de valeurs dans les DataTips épinglés.

    Lorsque les événements IntelliTrace et les instantanés est activé, IntelliTrace prendra un instantané du processus de l’application à chaque débogueur **point d’arrêt** et **étape** événement. Il enregistre les valeurs dans le **variables locales**, **automatique**, et **espion** windows, indépendamment de si les fenêtres sont ouvertes ou non. Les valeurs dans les DataTips épinglés seront également collectées.

- **Exceptions**

     IntelliTrace enregistre le type et le message d'exception pour ces types d'exceptions :

    - Exceptions traitées où l'exception est levée et interceptée

    - Exceptions non traitées

- **Événements .NET framework**

     Par défaut, IntelliTrace enregistre les événements .NET Framework les plus courants. Exemple :

    - Pour un événement de case à cocher, IntelliTrace collecte l'état et le texte de la case à cocher.

- **Événements d’application SharePoint 2010 et SharePoint 2013**

     Vous pouvez enregistrer des événements de profil utilisateur et un sous-ensemble d'événements ULS (Unified Logging System) pour les applications SharePoint 2010 et 2013 qui s'exécutent en dehors de Visual Studio. Vous pouvez enregistrer ces événements dans un fichier .iTrace. Requiert 2017 de Enterprise Visual Studio, Visual Studio Enterprise 2015, une version antérieure de Visual Studio Ultimate ou [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) en cours d’exécution **Trace** mode.

     Lorsque vous ouvrez le fichier .iTrace, vous pouvez entrer un ID de corrélation SharePoint pour rechercher sa requête web correspondante, afficher les événements inscrits, puis démarrer le débogage à partir d'un événement spécifique. Si le fichier contient des exceptions non gérées, vous pouvez choisir un ID de corrélation pour commencer à déboguer une exception.

     Consultez :

    - [Utiliser le collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

    - [Utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md)

    - [Procédure pas à pas : débogage d’une application SharePoint avec IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Capture d’instantanés**

Vous pouvez configurer IntelliTrace pour capturer des instantanés à chaque point d’arrêt et l’événement d’étape du débogueur. IntelliTrace enregistre l’état complet des applications à chaque instantané, ce qui vous permet d’afficher les variables complexes et pour évaluer les expressions.

Consultez [afficher des instantanés à l’aide d’IntelliTrace étape différée](../debugger/how-to-use-intellitrace-step-back.md).

**Collecter des informations sur les appels de fonction**

Configurez IntelliTrace pour collecter les informations sur les appels de fonctions. Ces informations vous permettent de consulter un historique de la pile des appels et d'exécuter en mode pas à pas des appels dans le code vers l'avant et vers l'arrière. Pour chaque appel de fonction, IntelliTrace enregistre les données suivantes :

- Nom de la fonction
- Valeurs des types de données primitifs passées comme paramètres aux points d'entrée de fonction et retournées aux points de sortie de fonction
- Valeurs des propriétés automatiques lorsqu'elles sont lues ou modifiées
- Pointeurs désignant des objets enfants de premier niveau, mais non leurs valeurs sauf si elles sont nulles ou pas

> [!NOTE]
> IntelliTrace collecte uniquement les 256 premiers objets des tableaux et les 256 premiers caractères des chaînes.

Consultez [Inspecter votre application avec débogage d’historique](../debugger/historical-debugging-inspect-app.md).

**Collecter des informations de module**

Pour contrôler la quantité d'informations sur les appels qu'IntelliTrace collecte, spécifiez uniquement les modules qui vous intéressent. Cela peut améliorer les performances de votre application pendant la collection. Consultez la section [contrôler la quantité d’informations IntelliTrace collecte](../debugger/intellitrace-features.md#ControlCallData) dans les fonctionnalités d’IntelliTrace.

## <a name="AffectPerformance"></a> IntelliTrace va ralentir mon application ?

Par défaut, IntelliTrace collecte uniquement les données des événements IntelliTrace sélectionnés. Votre application peut être ralentie ou non, en fonction de la structure et de l'organisation de votre code. Par exemple, si IntelliTrace enregistre souvent un événement, cela peut ralentir votre application. Cela peut aussi vous inciter à refactoriser votre application.

La collecte d'informations sur les appels peut ralentir votre application de manière significative. Cela peut également augmenter la taille des fichiers journaux IntelliTrace (.iTrace) que vous enregistrez sur le disque. Pour minimiser ces effets, collectez des informations sur les appels uniquement pour les modules qui vous intéressent.  Pour modifier la taille maximale de vos fichiers .iTrace, accédez à **outils**, **Options**, **IntelliTrace**, **avancé**. 

## <a name="in-this-section"></a>Dans cette section

[Fonctionnalités d’IntelliTrace](../debugger/intellitrace-features.md)
[diagnostiquer des problèmes après déploiement](../debugger/diagnose-problems-after-deployment.md)
[utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md)

### <a name="blogs"></a>Blogs

[Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)

### <a name="forums"></a>Forums

[Diagnostics Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)
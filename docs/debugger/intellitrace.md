---
title: IntelliTrace | Microsoft Docs
ms.date: 09/19/2018
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2be69003d14d2c246f95249b5db0b1fa7d470598
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911439"
---
# <a name="intellitrace-for-visual-studio-enterprise-c-visual-basic-c"></a>IntelliTrace pour Visual Studio Enterprise (C#, Visual Basic, C++)

Vous pouvez consacrer moins de temps au débogage de votre application quand vous utilisez IntelliTrace pour enregistrer et effectuer le suivi de l'historique d'exécution de votre code. Vous pouvez trouver des bogues facilement car IntelliTrace vous permet d'effectuer les tâches suivantes :

- enregistrer des événements spécifiques ;

- Examiner le code connexe, les données affichées dans la fenêtre **Variables locales** pendant les événements de débogueur et les informations sur les appels de fonction

- déboguer les erreurs qu'il est difficile de reproduire ou qui interviennent lors du déploiement.

Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise Edition (mais pas dans les éditions Professional ou Community).

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

|||
|-|-|
|**Déboguer mon application avec IntelliTrace :**<br /><br /> - Me montrer les événements passés.<br />- Me montrer les informations sur les appels avec les événements passés.<br />- Enregistrer ma session IntelliTrace.<br />- Vérifier les données collectées par IntelliTrace.|- [inspecter les États d’application précédents à l’aide d’IntelliTrace](../debugger/view-historical-application-state.md)<br />- [Procédure pas à pas : utilisation d’IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [Fonctionnalités IntelliTrace](../debugger/intellitrace-features.md)<br />- [Débogage d’historique](../debugger/historical-debugging.md)|
|**Collecter des données IntelliTrace à partir d'applications déployées**|- [Utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Démarrer le débogage à partir d'un fichier journal IntelliTrace (fichier .iTrace).**|- [Utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md)|

## <a name="IntelliTraceSupport"></a>Quelles applications peuvent être déboguées à l'aide d'IntelliTrace ?

| | |
|---------------------| - |
| **Prise en charge complète** | - Applications Visual Basic et Visual C# qui utilisent .NET Framework 2.0 ou versions ultérieures.<br/>Vous pouvez déboguer la plupart des applications, notamment ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010 et SharePoint 2013, ainsi que les applications 64 bits.<br/>Pour déboguer des applications SharePoint avec IntelliTrace, consultez [procédure pas à pas : débogage d’une application SharePoint à l’aide d’IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Pour déboguer des applications Microsoft Azure avec IntelliTrace, consultez [débogage d’un service Cloud publié avec IntelliTrace et Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md). |
| **Prise en charge limitée** | - C++ les applications ciblant Windows prennent en charge l’affichage des instantanés à l’aide d’IntelliTrace. Seuls les événements de débogueur et d’exception sont pris en charge.<br />-Applications .NET Core et ASP.NET Core prises en charge pour certains événements uniquement (événements du contrôleur MVC, ADO.NET et HTTPClient) dans le débogage local. Le collecteur autonome n’est pas pris en charge pour les applications .NET Core ou ASP.NET Core.<br />- Applications F# à titre expérimental<br />-Applications UWP prises en charge pour les événements uniquement |
| **Non pris en charge** | -Autres langages et scripts<br />-Windows Services, Silverlight, Xbox ou Windows Mobile Apps |

> [!NOTE]
> Si vous souhaitez déboguer un processus qui est déjà en cours d’exécution, vous pouvez collecter uniquement les événements IntelliTrace (aucune information sur les appels). Vous pouvez attacher à un processus 32 bits ou 64 bits sur l’ordinateur local uniquement. Les événements qui se produisent avant l’attachement au processus ne sont pas collectés.

## <a name="IntelliTraceVSTraditional"></a> Pourquoi déboguer à l'aide d'IntelliTrace ?

Qu'il soit traditionnel ou *en direct*, le débogage affiche uniquement l'état actuel de votre application avec des données limitées sur les événements passés. Vous devez déduire ces événements en fonction de l'état actuel de l'application ou recréer ces événements en réexécutant votre application.

IntelliTrace développe cette expérience de débogage traditionnel en enregistrant les événements et les données spécifiques à ces instants donnés dans le temps. Cela vous permet de voir ce qui s'est produit dans votre application sans la redémarrer, surtout si vous avez dépassé l'emplacement où se trouve le bogue. IntelliTrace est activé par défaut pendant un débogage traditionnel et collecte les données automatiquement et de façon invisible. Cela vous permet de basculer facilement entre le débogage traditionnel et le débogage IntelliTrace pour consulter les informations enregistrées. Consultez les [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md) et [Quelles sont les données collectées par IntelliTrace ?](#WhatData)

IntelliTrace peut également vous aider à déboguer des erreurs difficiles à reproduire ou celles qui se produisent lors du déploiement. Vous pouvez collecter les données IntelliTrace et les enregistrer dans un fichier journal IntelliTrace (fichier .iTrace). Un fichier .iTrace contient des informations détaillées sur les exceptions, les événements de performance, les requêtes web, les données de test, les threads, les modules et autres informations système. Vous pouvez ouvrir ce fichier dans Visual Studio Ultimate, sélectionner un élément et démarrer le débogage avec IntelliTrace. Cela vous permet d'accéder à n'importe quel événement dans le fichier et de consulter les détails spécifiques relatifs à votre application à ce moment-là.

Vous pouvez enregistrer les données IntelliTrace à partir des sources suivantes :

- Une session IntelliTrace dans Visual Studio 2015 Enterprise ou versions ultérieures, ou dans des versions antérieures de Visual Studio Ultimate.

- Applications Web ASP.NET hébergées sur IIS, ou applications SharePoint 2010 et SharePoint 2013 qui s'exécutent dans le déploiement lorsque vous utilisez Microsoft Monitoring Agent, seul ou conjointement à System Center 2012. Consultez [utiliser le collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) et la [surveillance avec Microsoft Monitoring agent](https://technet.microsoft.com/library/dn465153.aspx).

Voici quelques exemples pour vous aider à effectuer un débogage avec IntelliTrace :

- Votre application a endommagé un fichier de données, mais vous ignorez à quel emplacement cet événement s'est produit.

  Sans IntelliTrace, vous devez parcourir le code pour rechercher tous les accès possibles au fichier, placer des points d'arrêt sur ces accès, puis réexécuter votre application pour identifier l'emplacement où le problème s'est produit. Grâce à IntelliTrace, vous pouvez consulter tous les événements d'accès au fichier et des détails spécifiques relatifs à votre application quand chaque événement s'est produit.

- Une exception se produit.

  Sans IntelliTrace, vous recevez un message concernant une exception, mais vous avez peu d'informations relatives aux événements qui ont abouti à l'exception. Vous pouvez examiner la pile des appels pour consulter la chaîne des appels qui ont conduit à l'exception, mais ne pouvez pas consulter la séquence des événements qui s'est produite pendant ces appels. Grâce à IntelliTrace, vous pouvez examiner les événements antérieurs à l'exception.

- Un bogue ou un incident se produit dans une application déployée.

  Pour les applications basées sur Microsoft Azure, vous pouvez configurer la collection de données IntelliTrace avant de publier l’application. Pendant que votre application s'exécute, IntelliTrace enregistre les données dans un fichier .iTrace. Consultez [Déboguer un service Cloud publié avec IntelliTrace et Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).

  Pour les applications web ASP.NET hébergées sur IIS 7.0, 7.5 et 8.0, et les applications SharePoint 2010 ou SharePoint 2013, utilisez Microsoft Monitoring Agent, seul ou avec System Center 2012, pour enregistrer les données IntelliTrace dans un fichier .iTrace.

  Cela est utile lorsque vous souhaitez diagnostiquer les problèmes liés aux applications du déploiement. Consultez [utiliser le collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="WhatData"></a> Quelles sont les données collectées par IntelliTrace ?

**Collecter les informations sur les événements**

Par défaut, IntelliTrace enregistre uniquement les événements IntelliTrace : événements de débogueur, exceptions, événements .NET Framework et autres événements système qui peuvent vous aider lors d'un débogage. Déterminez le type d'événements qu'IntelliTrace doit collecter, à l'exception des événements et des exceptions du débogueur, qui sont collectés systématiquement. Consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).

- **Événements du débogueur**

  IntelliTrace enregistre systématiquement les événements intervenus dans le débogueur Visual Studio. Par exemple, le démarrage de votre application est un événement du débogueur. Les autres événements du débogueur sont les événements d'arrêt, qui interrompent l'exécution de votre application. Par exemple, votre programme atteint un point d'arrêt ou un point de trace, ou exécute une commande **Étape**.

  Par défaut, pour améliorer les performances, IntelliTrace n’enregistre pas toutes les valeurs possibles pour un événement du débogueur. En revanche, il enregistre les valeurs suivantes :

  - Valeurs de la fenêtre **Variables locales**. Gardez la fenêtre **Variables locales** ouverte pour afficher ces valeurs.

  - Valeurs dans la fenêtre **Automatique** uniquement si **elle** est ouverte

  - Valeurs situées dans DataTips qui apparaissent lorsque vous déplacez le pointeur de la souris au-dessus d'une variable dans la fenêtre source pour afficher sa valeur. IntelliTrace ne collecte pas de valeurs dans les DataTips épinglés.

    Quand les événements IntelliTrace et le mode instantanés sont activés, IntelliTrace prend un instantané du processus de l’application à chaque **point d’arrêt** et événement d' **étape** du débogueur. Cela permet d’enregistrer des valeurs dans les fenêtres **variables locales**, **automatique**et **Espion** , que les fenêtres soient ouvertes ou non. Les valeurs des info-bulles de données épinglées sont également collectées.

- **Exceptions**

  IntelliTrace enregistre le type et le message d'exception pour ces types d'exceptions :

  - Exceptions traitées où l'exception est levée et interceptée

  - Exceptions non traitées

- **Événements .NET Framework**

  Par défaut, IntelliTrace enregistre les événements .NET Framework les plus courants. Par exemple, pour un événement <xref:System.Windows.Forms.CheckBox.CheckedChanged?displayProperty=nameWithType>, IntelliTrace collecte l’État et le texte de la case à cocher.

- **Événements d'application SharePoint 2010 et SharePoint 2013**

  Vous pouvez enregistrer des événements de profil utilisateur et un sous-ensemble d'événements ULS (Unified Logging System) pour les applications SharePoint 2010 et 2013 qui s'exécutent en dehors de Visual Studio. Vous pouvez enregistrer ces événements dans un fichier .iTrace. Requiert Visual Studio Enterprise 2015 ou versions ultérieures, une version précédente de Visual Studio Ultimate ou [Microsoft Monitoring agent](https://www.microsoft.com/download/details.aspx?id=40316) s’exécutant en mode **trace** .

  Lorsque vous ouvrez le fichier .iTrace, vous pouvez entrer un ID de corrélation SharePoint pour rechercher sa requête web correspondante, afficher les événements inscrits, puis démarrer le débogage à partir d'un événement spécifique. Si le fichier contient des exceptions non gérées, vous pouvez choisir un ID de corrélation pour commencer à déboguer une exception.

  Consultez :

  - [Utiliser le collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

  - [Utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md)

  - [Procédure pas à pas : débogage d’une application SharePoint avec IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Capturer des instantanés**

Vous pouvez configurer IntelliTrace pour capturer des instantanés à chaque point d’arrêt et événement d’étape du débogueur. IntelliTrace enregistre l’état complet de l’application sur chaque instantané, ce qui vous permet d’afficher des variables complexes et d’évaluer des expressions.

> [!NOTE]
> Le [collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) ne prend pas en charge la capture d’instantanés.

Consultez [inspecter les États d’application précédents à l’aide d’IntelliTrace](../debugger/view-historical-application-state.md).

**Collecter les informations sur les appels de fonction**

Configurez IntelliTrace pour collecter les informations sur les appels de fonctions. Ces informations vous permettent de consulter un historique de la pile des appels et d'exécuter en mode pas à pas des appels dans le code vers l'avant et vers l'arrière. Pour chaque appel de fonction, IntelliTrace enregistre les données suivantes :

- Nom de la fonction
- Valeurs des types de données primitifs passées comme paramètres aux points d'entrée de fonction et retournées aux points de sortie de fonction
- Valeurs des propriétés automatiques lorsqu'elles sont lues ou modifiées
- Pointeurs désignant des objets enfants de premier niveau, mais non leurs valeurs sauf si elles sont nulles ou pas

> [!NOTE]
> IntelliTrace collecte uniquement les 256 premiers objets des tableaux et les 256 premiers caractères des chaînes.

Consultez [inspecter votre application avec le débogage d’historique](../debugger/historical-debugging-inspect-app.md).

**Collecter les informations de module**

Pour contrôler la quantité d'informations sur les appels qu'IntelliTrace collecte, spécifiez uniquement les modules qui vous intéressent. Cela peut améliorer les performances de votre application pendant la collecte. Consultez la section [contrôler la quantité d’informations collectées par IntelliTrace](../debugger/intellitrace-features.md#ControlCallData) dans les fonctionnalités IntelliTrace.

## <a name="AffectPerformance"></a> Mon application peut-elle être ralentie par IntelliTrace ?

Par défaut, IntelliTrace collecte uniquement les données des événements IntelliTrace sélectionnés. Votre application peut être ralentie ou non, en fonction de la structure et de l'organisation de votre code. Par exemple, si IntelliTrace enregistre souvent un événement, cela peut ralentir votre application. Cela peut aussi vous inciter à refactoriser votre application.

La collecte d'informations sur les appels peut ralentir votre application de manière significative. Cela peut également augmenter la taille des fichiers journaux IntelliTrace (.iTrace) que vous enregistrez sur le disque. Pour minimiser ces effets, collectez des informations sur les appels uniquement pour les modules qui vous intéressent.  Pour modifier la taille maximale de vos fichiers .iTrace, accédez à **Outils**, **Options**, **IntelliTrace**, **Avancé**.

### <a name="blogs"></a>Blogs

[Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Forums

[Diagnostics Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)

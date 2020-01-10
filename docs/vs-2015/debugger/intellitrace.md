---
title: IntelliTrace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 142
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db7430d03bbce065b75e890736253c6ba05752d0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298919"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La dernière version de cette rubrique est disponible dans [IntelliTrace](https://docs.microsoft.com/visualstudio/debugger/intellitrace) .  
  
Vous pouvez consacrer moins de temps au débogage de votre application quand vous utilisez IntelliTrace pour enregistrer et effectuer le suivi de l'historique d'exécution de votre code. Vous pouvez trouver des bogues facilement car IntelliTrace vous permet d'effectuer les tâches suivantes :  
  
- enregistrer des événements spécifiques ;  
  
   Examiner le code connexe, les données affichées dans la fenêtre **Variables locales** pendant les événements de débogueur et les informations sur les appels de fonction  
  
- déboguer les erreurs qu'il est difficile de reproduire ou qui interviennent lors du déploiement.  
  
  Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise Edition (mais pas dans les éditions Professional ou Community).  
  
## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?  
  
|||  
|-|-|  
|**Déboguer mon application avec IntelliTrace :**<br /><br /> -Afficher les événements passés.<br />-Afficher les informations sur les appels avec des événements passés.<br />-Enregistrer ma session IntelliTrace.<br />-Contrôler les données collectées par IntelliTrace.|-   [Procédure pas à pas : utilisation d’IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [Fonctionnalités IntelliTrace](../debugger/intellitrace-features.md)<br />-   [configurer IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [Débogage d’historique](../debugger/historical-debugging.md)|  
|**Collecter les données IntelliTrace pendant une session de test dans Test Manager**|-   [Collecter plus de données de diagnostic dans des tests manuels](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
|**Collecter des données IntelliTrace à partir d'applications déployées**|-   [Utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Démarrer le débogage à partir d'un fichier journal IntelliTrace (fichier .iTrace).**|-   [Utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md)|  
  
## <a name="IntelliTraceSupport"></a>Quelles applications peuvent être déboguées à l'aide d'IntelliTrace ?  
  
|||  
|-|-|  
|**Prise en charge**|-Les applications Visual Basic C# et visuelles qui utilisent .NET Framework version 2,0 ou ultérieure.<br />     Vous pouvez déboguer la plupart des applications, notamment ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010 et SharePoint 2013, ainsi que les applications 64 bits.<br />     Pour déboguer des applications SharePoint avec IntelliTrace, consultez [procédure pas à pas : débogage d’une application SharePoint à l’aide d’IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4).<br />     Pour déboguer des applications Microsoft Azure avec IntelliTrace, consultez [débogage d’un service Cloud publié avec IntelliTrace et Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).|  
|**Prise en charge limitée**|- F# applications sur une base expérimentale<br />-Applications du Windows Store prises en charge pour les événements uniquement|  
|**Non pris en charge**|- C++, autres langages et script<br />-Windows Services, Silverlight, Xbox ou [!INCLUDE[winmobile](../includes/winmobile-md.md)] apps|  
  
> [!NOTE]
> Si vous souhaitez déboguer un processus qui est déjà en cours d'exécution, vous ne pouvez pas utiliser IntelliTrace. Vous devez démarrer IntelliTrace lorsque le processus commence.  
  
## <a name="IntelliTraceVSTraditional"></a> Pourquoi déboguer à l'aide d'IntelliTrace ?  
 Qu'il soit traditionnel ou *en direct*, le débogage affiche uniquement l'état actuel de votre application avec des données limitées sur les événements passés. Vous devez déduire ces événements en fonction de l'état actuel de l'application ou recréer ces événements en réexécutant votre application.  
  
 IntelliTrace développe cette expérience de débogage traditionnel en enregistrant les événements et les données spécifiques à ces instants donnés dans le temps. Cela vous permet de voir ce qui s'est produit dans votre application sans la redémarrer, surtout si vous avez dépassé l'emplacement où se trouve le bogue. IntelliTrace est activé par défaut pendant un débogage traditionnel et collecte les données automatiquement et de façon invisible. Cela vous permet de basculer facilement entre le débogage traditionnel et le débogage IntelliTrace pour consulter les informations enregistrées. Consultez les [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md) et [Quelles sont les données collectées par IntelliTrace ?](#WhatData)  
  
 IntelliTrace peut également vous aider à déboguer des erreurs difficiles à reproduire ou celles qui se produisent lors du déploiement. Vous pouvez collecter les données IntelliTrace et les enregistrer dans un fichier journal IntelliTrace (fichier .iTrace). Un fichier .iTrace contient des informations détaillées sur les exceptions, les événements de performance, les requêtes web, les données de test, les threads, les modules et autres informations système. Vous pouvez ouvrir ce fichier dans Visual Studio Ultimate, sélectionner un élément et démarrer le débogage avec IntelliTrace. Cela vous permet d'accéder à n'importe quel événement dans le fichier et de consulter les détails spécifiques relatifs à votre application à ce moment-là.  
  
 Vous pouvez enregistrer les données IntelliTrace à partir des sources suivantes :  
  
- Une session IntelliTrace dans Visual Studio 2015 Enterprise ou dans des versions antérieures de Visual Studio Ultimate.  
  
- Une session de test dans Microsoft Test Manager.  
  
- Applications Web ASP.NET hébergées sur IIS, ou applications SharePoint 2010 et SharePoint 2013 qui s'exécutent dans le déploiement lorsque vous utilisez Microsoft Monitoring Agent, seul ou conjointement à System Center 2012. Consultez [utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) et [surveillance avec Microsoft Monitoring agent](https://technet.microsoft.com/library/dn465153.aspx).  
  
  Voici quelques exemples pour vous aider à effectuer un débogage avec IntelliTrace :  
  
- Votre application a endommagé un fichier de données, mais vous ignorez à quel emplacement cet événement s'est produit.  
  
   Sans IntelliTrace, vous devez parcourir le code pour rechercher tous les accès possibles au fichier, placer des points d'arrêt sur ces accès, puis réexécuter votre application pour identifier l'emplacement où le problème s'est produit. Grâce à IntelliTrace, vous pouvez consulter tous les événements d'accès au fichier et des détails spécifiques relatifs à votre application quand chaque événement s'est produit.  
  
- Une exception se produit.  
  
   Sans IntelliTrace, vous recevez un message concernant une exception, mais vous avez peu d'informations relatives aux événements qui ont abouti à l'exception. Vous pouvez examiner la pile des appels pour consulter la chaîne des appels qui ont conduit à l'exception, mais ne pouvez pas consulter la séquence des événements qui s'est produite pendant ces appels. Grâce à IntelliTrace, vous pouvez examiner les événements antérieurs à l'exception.  
  
- Votre application se bloque sur un ordinateur de test, mais s'exécute correctement sur un ordinateur de développement.  
  
   Vous pouvez collecter les données IntelliTrace avec Microsoft Test Manager, enregistrer les données dans un fichier .iTrace et attacher ce fichier à un élément de travail Team Foundation Server pour un examen approfondi. Consultez [collecter plus de données de diagnostic dans les tests manuels](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) et [utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md).  
  
- Un bogue ou un incident se produit dans une application déployée.  
  
   Pour les applications basées sur Microsoft Azure, vous pouvez configurer la collection de données IntelliTrace avant de publier l’application. Pendant que votre application s'exécute, IntelliTrace enregistre les données dans un fichier .iTrace. Consultez [Débogage d’un service cloud publié avec IntelliTrace et Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).  
  
   Pour les applications web ASP.NET hébergées sur IIS 7.0, 7.5 et 8.0, et les applications SharePoint 2010 ou SharePoint 2013, utilisez Microsoft Monitoring Agent, seul ou avec System Center 2012, pour enregistrer les données IntelliTrace dans un fichier .iTrace.  
  
   Cela est utile lorsque vous souhaitez diagnostiquer les problèmes liés aux applications du déploiement. Consultez [utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="WhatData"></a> Quelles sont les données collectées par IntelliTrace ?  
 **Collecte des informations sur les événements**  
  
 Par défaut, IntelliTrace enregistre uniquement les événements IntelliTrace : événements de débogueur, exceptions, événements .NET Framework et autres événements système qui peuvent vous aider lors d'un débogage. Déterminez le type d'événements qu'IntelliTrace doit collecter, à l'exception des événements et des exceptions du débogueur, qui sont collectés systématiquement. Consultez [configurer IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
- **Événements du débogueur**  
  
   IntelliTrace enregistre systématiquement les événements intervenus dans le débogueur Visual Studio. Par exemple, le démarrage de votre application est un événement du débogueur. Les autres événements du débogueur sont les événements d'arrêt, qui interrompent l'exécution de votre application. Par exemple, votre programme atteint un point d'arrêt ou un point de trace, ou exécute une commande **Étape**.  
  
   Pour améliorer les performances, IntelliTrace n'enregistre pas toutes les valeurs possibles pour un événement du débogueur. En revanche, il enregistre les valeurs suivantes :  
  
  - Valeurs de la fenêtre **Variables locales**. Gardez la fenêtre **Variables locales** ouverte pour afficher ces valeurs.  
  
  - Valeurs dans la fenêtre **Automatique** uniquement si **elle** est ouverte  
  
  - Valeurs situées dans DataTips qui apparaissent lorsque vous déplacez le pointeur de la souris au-dessus d'une variable dans la fenêtre source pour afficher sa valeur. IntelliTrace ne collecte pas de valeurs dans les DataTips épinglés.  
  
- **Exceptions**  
  
   IntelliTrace enregistre le type et le message d'exception pour ces types d'exceptions :  
  
  - Exceptions traitées où l'exception est levée et interceptée  
  
  - Exceptions non traitées  
  
- **Événements .NET Framework**  
  
   Par défaut, IntelliTrace enregistre les événements .NET Framework les plus courants. Exemple :  
  
  - Pour un événement d'accès au fichier, IntelliTrace collecte le nom de fichier.  
  
  - Pour un événement de case à cocher, IntelliTrace collecte l'état et le texte de la case à cocher.  
  
- **Événements d'application SharePoint 2010 et SharePoint 2013**  
  
   Vous pouvez enregistrer des événements de profil utilisateur et un sous-ensemble d'événements ULS (Unified Logging System) pour les applications SharePoint 2010 et 2013 qui s'exécutent en dehors de Visual Studio. Vous pouvez enregistrer ces événements dans un fichier .iTrace. Requiert Visual Studio Enterprise 2015, une version précédente de Visual Studio Ultimate ou [Microsoft Monitoring agent](https://go.microsoft.com/fwlink/?LinkId=320384) s’exécutant en mode **trace** .  
  
   Lorsque vous ouvrez le fichier .iTrace, vous pouvez entrer un ID de corrélation SharePoint pour rechercher sa requête web correspondante, afficher les événements inscrits, puis démarrer le débogage à partir d'un événement spécifique. Si le fichier contient des exceptions non gérées, vous pouvez choisir un ID de corrélation pour commencer à déboguer une exception.  
  
   Reportez-vous à :  
  
  - [Utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
  - [Utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md)  
  
  - [Procédure pas à pas : débogage d’une application SharePoint avec IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
  **Collecte d’informations sur les appels de fonction**  
  
  Configurez IntelliTrace pour collecter les informations sur les appels de fonctions. Ces informations vous permettent de consulter un historique de la pile des appels et d'exécuter en mode pas à pas des appels dans le code vers l'avant et vers l'arrière. Pour chaque appel de fonction, IntelliTrace enregistre les données suivantes :  
  
- Nom de la fonction  
  
- Valeurs des types de données primitifs passées comme paramètres aux points d'entrée de fonction et retournées aux points de sortie de fonction  
  
- Valeurs des propriétés automatiques lorsqu'elles sont lues ou modifiées  
  
- Pointeurs désignant des objets enfants de premier niveau, mais non leurs valeurs sauf si elles sont nulles ou pas  
  
> [!NOTE]
> IntelliTrace collecte uniquement les 256 premiers objets des tableaux et les 256 premiers caractères des chaînes.  
  
 Consultez [configurer IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 **Collecte d’informations sur le module**  
  
 Pour contrôler la quantité d'informations sur les appels qu'IntelliTrace collecte, spécifiez uniquement les modules qui vous intéressent. Cela peut améliorer les performances de votre application pendant la collecte. Consultez [configurer IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="AffectPerformance"></a> Mon application peut-elle être ralentie par IntelliTrace ?  
 Par défaut, IntelliTrace collecte uniquement les données des événements IntelliTrace sélectionnés. Votre application peut être ralentie ou non, en fonction de la structure et de l'organisation de votre code. Par exemple, si IntelliTrace enregistre souvent un événement, cela peut ralentir votre application. Cela peut aussi vous inciter à refactoriser votre application.  
  
 La collecte d'informations sur les appels peut ralentir votre application de manière significative. Cela peut également augmenter la taille des fichiers journaux IntelliTrace (.iTrace) que vous enregistrez sur le disque. Pour minimiser ces effets, collectez des informations sur les appels uniquement pour les modules qui vous intéressent.  Pour modifier la taille maximale de vos fichiers .iTrace, accédez à **Outils**, **Options**, **IntelliTrace**, **Avancé**. Consultez [configurer IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Fonctionnalités IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Configurer IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Inclusion de données de trace de diagnostic avec des bogues difficiles à reproduire](https://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [Diagnostiquer des problèmes après le déploiement](../debugger/diagnose-problems-after-deployment.md)  
  
 [Utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>Blogs  
 [Visual Studio ALM + Team Foundation Server](https://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>Forums  
 [Diagnostics Visual Studio](https://go.microsoft.com/fwlink/?LinkId=262263)

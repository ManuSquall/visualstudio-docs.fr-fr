---
title: "Fonctionnalités d’IntelliTrace | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 01515701b6aeecc1166551c6376bfd6823e73976
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="intellitrace-features"></a>Fonctionnalités IntelliTrace

Vous pouvez utiliser IntelliTrace pour enregistrer les événements et les appels de méthode dans votre application, ce qui vous permet d'examiner son état (pile des appels et valeurs des variables locales) à différents stades de l'exécution. Commencez le débogage comme d’habitude - IntelliTrace est activé par défaut, et vous pouvez voir les informations enregistrées sont affichées dans la nouvelle **outils de Diagnostic** fenêtre sous le **événements** onglet. Sélectionnez un événement et cliquez sur **activer le débogage d’historique** pour afficher la pile des appels et les variables locales enregistrées pour cet événement.

Pour obtenir une description étape par étape, consultez [procédure pas à pas : à l’aide de IntelliTrace](../debugger/walkthrough-using-intellitrace.md).

IntelliTrace est disponible dans Visual Studio Enterprise Edition, mais pas dans les éditions Visual Studio Professional ou Community.

Pour confirmer qu’IntelliTrace est activé, ouvrez le **Outils > Options > IntelliTrace** page d’options. **Activer IntelliTrace** doit être activée par défaut.

> [!NOTE]
> L’étendue de tous les paramètres sur le **IntelliTrace** page d’options est Visual Studio en tant qu’entier, pas les projets ou solutions. Une modification de ces paramètres s'applique à toutes les instances de Visual Studio, à toutes les sessions de débogage et à tous les projets ou solutions.

## <a name="ChooseEvents"></a> Choisir les événements qu’IntelliTrace enregistre

Vous pouvez activer ou désactiver l’enregistrement d’événements IntelliTrace spécifiques.

Si vous êtes en cours de débogage, interrompez-le. Accédez à **Outils > Options > IntelliTrace > événements IntelliTrace**. Choisissez les événements IntelliTrace à enregistrer.

## <a name="Snapshots"></a> Collectez des événements et des captures instantanées

Cette option n’est pas activée par défaut, mais IntelliTrace peut capturer des instantanés de votre application à chaque événement d’étape de point d’arrêt et le débogueur, et vous pouvez afficher les instantanés AlwaysOn dans une session de débogage historique. Un instantané vous donne un aperçu de votre état complet des applications. Pour activer la capture d’instantanés, accédez à **Outils > Options > IntelliTrace > Général**, puis sélectionnez **IntelliTrace événements et les instantanés**. Pour plus d’informations, consultez [afficher des instantanés à l’aide d’IntelliTrace étape différée](../debugger/how-to-use-intellitrace-step-back.md)

Les instantanés sont disponibles dans Visual Studio de Enterprise 2017 15,5 et versions ultérieures, et nécessite le mise à jour anniversaire Windows 10 ou version ultérieure.  Pour les applications .NET Core et ASP.NET Core, 2017 de Enterprise Visual Studio version 15,7 version préliminaire 1 est requis.

## <a name="GoingFurther"></a> Collecter des événements IntelliTrace et informations d’appels

Cette option n’est pas activée par défaut, mais IntelliTrace peut enregistrer les appels de méthode avec des événements. Pour activer la collecte d’atteindre des appels de méthode **Outils > Options > IntelliTrace > Général**, puis sélectionnez **événements IntelliTrace et informations d’appels**.

Informations sur les appels ne sont pas actuellement disponibles pour les applications .NET Core et ASP.NET Core. 

Cette opération vous permet de consulter l'historique de la pile des appels et de vous déplacer vers l'arrière ou vers l'avant dans les appels de votre code. IntelliTrace enregistre des données comme les noms des méthodes, les points d'entrée et de sortie des méthodes, ainsi que certaines valeurs de paramètres et de retour.

> [!TIP]
> Cette option n'est pas activée par défaut, car elle ajoute une charge considérable. Non seulement IntelliTrace doit intercepter chaque appel de méthode effectué par votre application, mais il doit également gérer un ensemble beaucoup plus vaste de données en ce qui concerne l'affichage à l'écran ou la conservation sur disque.
>
> Vous pouvez réduire la surcharge de performances en limitant la liste des événements enregistrés par IntelliTrace et en réduisant au minimum le nombre de modules que vous collectez. Pour plus d’informations, consultez [contrôle combien informations sur les appels IntelliTrace enregistre](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Utilisez la marge de navigation

Vous pouvez utiliser la marge de navigation affichée à gauche de la fenêtre de code. Si vous ne voyez pas la marge de navigation, accédez à **Outils > Options > IntelliTrace > Avancé**, puis sélectionnez **afficher la marge de navigation en mode débogage**.

La marge de navigation vous permet de vous déplacer vers l'avant et vers l'arrière parmi les appels de méthode et les événements en mode de débogage d'historique. Pour plus d’informations sur le débogage d’historique, consultez [le débogage d’historique](../debugger/historical-debugging.md). Elle comporte plusieurs commandes :

|||
|-|-|
|**Définir le contexte du débogueur ici**|Définissez le contexte du débogueur en fonction du moment auquel apparaît l'appel.<br /><br /> Cette icône apparaît uniquement sur la pile des appels actuelle.|
|**Revenir au Site d’appel**|Déplacez le pointeur et le contexte de débogage en remontant jusqu'au moment où la fonction active a été appelée.<br /><br /> Si vous êtes en mode de débogage réel cette commande active le débogage d'historique. Si vous revenez à l'arrêt d'exécution d'origine, le débogage d'historique est désactivé et le débogage réel est activé.|
|**Aller à l’appel précédent ou l’événement IntelliTrace**|Déplacez le pointeur et le contexte de débogage en remontant jusqu'à l'appel ou l'événement précédent.<br /><br /> Si vous êtes en mode de débogage réel, cette commande active le débogage d'historique.|
|**L’étape**|Effectuer un pas à pas détaillé dans la fonction sélectionnée.<br /><br /> Cette commande est disponible uniquement quand vous êtes en mode de débogage d'historique.|
|**Accédez au prochain appel ou l’événement IntelliTrace**|Déplacez le pointeur et le contexte de débogage en avançant jusqu'à l'appel ou l'événement suivant pour lequel il existe des données IntelliTrace.<br /><br /> Cette commande est disponible uniquement quand vous êtes en mode de débogage d'historique.|
|**Aller à Mode réel**|Revenir au débogage réel|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>Rechercher une ligne ou une méthode dans IntelliTrace

Vous pouvez rechercher des méthodes uniquement quand les informations sur les appels de méthode ont été activées. Vous pouvez consulter l'historique d'IntelliTrace à la recherche d'une ligne ou d'une méthode spécifique. Lorsque l’exécution du débogueur est interrompue, avec le bouton droit dans le corps de la fonction pour afficher le menu contextuel et cliquez sur **rechercher cette ligne dans IntelliTrace** ou **rechercher cette méthode dans IntelliTrace**.

### <a name="ControlCallData"></a> Vérifier la quantité d’informations d’appels IntelliTrace enregistre

Par défaut, IntelliTrace enregistre des informations pour tous les modules utilisés par votre solution. Vous pouvez configurer IntelliTrace pour qu'il enregistre des informations sur les appels uniquement pour les modules qui vous intéressent. Dans **Outils > Options > IntelliTrace > Modules**, vous pouvez spécifier les modules à inclure ou à exclure d’IntelliTrace. IntelliTrace recueille uniquement les événements provenant des modules que vous avez spécifiés et les appels de méthode qui se sont produits dans les modules qui vous intéressent.

Pour ajouter plusieurs modules, utilisez le caractère générique * au début ou à la fin de la chaîne. Pour les noms de modules, utilisez des noms de fichiers, et non des noms d'assemblys. Les chemins d’accès de fichiers ne sont pas acceptés.

Essayez de réduire le nombre de modules au minimum. Vous obtiendrez de meilleures performances car il y aura moins de données à recueillir. Vous obtiendrez également moins de bruit dans l'interface utilisateur car il y aura moins de données à parcourir.

## <a name="SaveSession"></a> Enregistrer les données IntelliTrace au fichier

Vous pouvez enregistrer les données recueillies par IntelliTrace va **Déboguer > IntelliTrace > Enregistrer la IntelliTrace Session** pendant que vous déboguez et que l’application est dans un état d’arrêt. L'élément de menu est désactivé et vous ne pourrez pas enregistrer les données recueillies par IntelliTrace si l'application est encore en cours d'exécution ou si vous avez arrêté le débogage.

Vous pouvez configurer IntelliTrace pour enregistrer automatiquement dans un fichier en accédant à **Outils > Options > IntelliTrace > Avancé** et en sélectionnant **stocker les enregistrements IntelliTrace dans ce répertoire**. Vous pouvez aussi configurer une taille fixe pour le fichier généré. Dans ce cas, IntelliTrace remplace les anciennes données quand l'espace libre est insuffisant. Visual Studio crée deux fichiers pour chaque session IntelliTrace quand elles sont enregistrées automatiquement et que le processus d'hébergement Visual Studio (vshost.exe) est activé.

> [!TIP]
> Pour économiser l’espace disque, désactivez l’enregistrement de fichiers automatiquement lorsque vous n’en avez plus besoin. Les fichiers existants ne seront pas supprimés. Vous pouvez toujours enregistrer les données dans un fichier à la demande à partir du menu contextuel.

Quand vous enregistrez des données IntelliTrace dans un fichier, vous obtenez un fichier .itrace pour chaque processus à partir duquel IntelliTrace a recueilli des données. Vous pouvez ensuite ouvrir le fichier .itrace dans Visual Studio en accédant à **fichier > Ouvrir > fichier** et en sélectionnant le fichier .itrace à partir de la boîte de dialogue Ouvrir un fichier. Pour plus d’informations, consultez [à l’aide des données IntelliTrace enregistrée](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Blogs

[IntelliTrace dans Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)

[Procédure pas à pas de débogage réel à l’aide d’IntelliTrace dans Visual Studio 2015 (éditeur de texte)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)

[Procédure pas à pas de débogage réel à l’aide d’IntelliTrace dans Visual Studio 2015 (Social Club)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)

[IntelliTrace dans Visual Studio Enterprise 2015 maintenant prend en charge l’attachement !](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)

[Collecter des données à partir d’un service windows à l’aide du collecteur autonome IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)

[Modifier le plan de collecte IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)

[TraceSource personnalisés et débogage à l’aide d’IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)

[En cours d’exécution collecteur autonome IntelliTrace et les Pools d’applications sous des comptes Active Directory](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)

## <a name="forums"></a>Forums

[Débogueur Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)

## <a name="videos"></a>Vidéos

[Expérience d’IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)

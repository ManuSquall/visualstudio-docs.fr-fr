---
title: Fonctionnalités IntelliTrace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: 73
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dc16094c98a912d073bd6b873ecb3d1b3b411d1e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298945"
---
# <a name="intellitrace-features"></a>Fonctionnalités IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser IntelliTrace pour enregistrer les événements et les appels de méthode dans votre application, ce qui vous permet d'examiner son état (pile des appels et valeurs des variables locales) à différents stades de l'exécution. Commencez simplement le débogage comme d’habitude-IntelliTrace est activé par défaut, et vous pouvez voir les informations enregistrées par IntelliTrace dans la fenêtre nouveau **outils de diagnostic** sous l’onglet **événements** . Sélectionnez un événement et cliquez sur **activer le débogage d’historique** pour afficher la pile des appels et les variables locales enregistrées pour cet événement.  
  
 Pour obtenir une description étape par étape, consultez [Procédure pas à pas : utilisation d'IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 IntelliTrace est disponible dans Visual Studio Enterprise Edition, mais pas dans les éditions Visual Studio Professional ou Community.  
  
 Pour confirmer qu'IntelliTrace est activé, ouvrez la page d'options **Outils / Options / IntelliTrace**. L’option **Activer IntelliTrace** doit être activée par défaut.  
  
> [!NOTE]
> L’étendue de tous les paramètres dans la page d’options **IntelliTrace** est Visual Studio tout entier, et non pas des projets ou des solutions spécifiques. Une modification de ces paramètres s'applique à toutes les instances de Visual Studio, à toutes les sessions de débogage et à tous les projets ou solutions.  
  
## <a name="ChooseEvents"></a>Choisir les événements qu’IntelliTrace enregistre  
 Vous pouvez activer ou désactiver l'enregistrement d'événements IntelliTrace spécifiques.  
  
 Si vous êtes en cours de débogage, interrompez-le. Accédez à **Outils / Options / IntelliTrace / Événements IntelliTrace**. Choisissez les événements IntelliTrace à enregistrer.  
  
## <a name="GoingFurther"></a>Collecter les événements IntelliTrace et les informations sur les appels  
 Cette fonctionnalité n'est pas activée par défaut, mais IntelliTrace peut enregistrer les appels de méthode en plus des événements. Pour activer la collecte des appels de méthode, accédez à  **Outils / Options / IntelliTrace / Général**, puis sélectionnez **Événements IntelliTrace et informations d'appel**.  
  
 Cette opération vous permet de consulter l'historique de la pile des appels et de vous déplacer vers l'arrière ou vers l'avant dans les appels de votre code. IntelliTrace enregistre des données comme les noms des méthodes, les points d'entrée et de sortie des méthodes, ainsi que certaines valeurs de paramètres et de retour.  
  
> [!TIP]
> Cette option n'est pas activée par défaut, car elle ajoute une charge considérable. Non seulement IntelliTrace doit intercepter chaque appel de méthode effectué par votre application, mais il doit également gérer un ensemble beaucoup plus vaste de données en ce qui concerne l'affichage à l'écran ou la conservation sur disque.  
>   
> Vous pouvez réduire la surcharge de performances en limitant la liste des événements enregistrés par IntelliTrace et en réduisant au minimum le nombre de modules que vous collectez. Pour plus d’informations, consultez [Vérifier le nombre d’informations sur les appels qu’IntelliTrace enregistre](../debugger/intellitrace-features.md#ControlCallData).  
  
### <a name="using-the-navigation-gutter"></a>Utilisation de la marge de navigation  
 Vous pouvez utiliser la marge de navigation affichée à gauche de la fenêtre de code. Si la marge de navigation n'est pas visible, accédez à **Outils / Options / IntelliTrace / Avancé**, puis sélectionnez **Afficher la marge de navigation en mode débogage**.  
  
 La marge de navigation vous permet de vous déplacer vers l'avant et vers l'arrière parmi les appels de méthode et les événements en mode de débogage d'historique. Pour plus d’informations sur le débogage d’historique, consultez [Débogage d’historique](../debugger/historical-debugging.md). Elle comporte plusieurs commandes :  
  
|||  
|-|-|  
|**Définir le contexte du débogueur ici**|Définissez le contexte du débogueur en fonction du moment auquel apparaît l'appel.<br /><br /> Cette icône apparaît uniquement sur la pile des appels actuelle.|  
|**Revenir au site d’appel**|Déplacez le pointeur et le contexte de débogage en remontant jusqu'au moment où la fonction active a été appelée.<br /><br /> Si vous êtes en mode de débogage réel cette commande active le débogage d'historique. Si vous revenez à l'arrêt d'exécution d'origine, le débogage d'historique est désactivé et le débogage réel est activé.|  
|**Aller à l’appel ou l’événement IntelliTrace précédent**|Déplacez le pointeur et le contexte de débogage en remontant jusqu'à l'appel ou l'événement précédent.<br /><br /> Si vous êtes en mode de débogage réel, cette commande active le débogage d'historique.|  
|**Pas à pas détaillé**|Effectuer un pas à pas détaillé dans la fonction sélectionnée.<br /><br /> Cette commande est disponible uniquement quand vous êtes en mode de débogage d'historique.|  
|**Aller à l’appel ou l’événement IntelliTrace suivant**|Déplacez le pointeur et le contexte de débogage en avançant jusqu'à l'appel ou l'événement suivant pour lequel il existe des données IntelliTrace.<br /><br /> Cette commande est disponible uniquement quand vous êtes en mode de débogage d'historique.|  
|**Aller à Mode réel**|Revenir au débogage réel|  
  
### <a name="search-for-a-line-or-method-in-intellitrace"></a>Rechercher une ligne ou une méthode dans IntelliTrace  
 Vous pouvez rechercher des méthodes uniquement quand les informations sur les appels de méthode ont été activées. Vous pouvez consulter l'historique d'IntelliTrace à la recherche d'une ligne ou d'une méthode spécifique. Quand l’exécution du débogueur est interrompue, cliquez avec le bouton droit dans le corps de la fonction pour afficher le menu contextuel et cliquez sur **Rechercher cette ligne dans IntelliTrace** ou **Rechercher cette méthode dans IntelliTrace**.  
  
### <a name="ControlCallData"></a> Vérifier le nombre d’informations sur les appels qu’IntelliTrace enregistre  
 Par défaut, IntelliTrace enregistre des informations pour tous les modules utilisés par votre solution. Vous pouvez configurer IntelliTrace pour qu'il enregistre des informations sur les appels uniquement pour les modules qui vous intéressent. Dans **Outils / Options / IntelliTrace / Modules**, vous pouvez spécifier les modules à inclure ou à exclure d'IntelliTrace. IntelliTrace recueille uniquement les événements provenant des modules que vous avez spécifiés et les appels de méthode qui se sont produits dans les modules qui vous intéressent.  
  
 Pour ajouter plusieurs modules, utilisez le caractère générique * au début ou à la fin de la chaîne. Pour les noms de modules, utilisez des noms de fichiers, et non des noms d'assemblys. Les chemins d’accès de fichiers ne sont pas acceptés.  
  
 Essayez de réduire le nombre de modules au minimum. Vous obtiendrez de meilleures performances car il y aura moins de données à recueillir. Vous obtiendrez également moins de bruit dans l'interface utilisateur car il y aura moins de données à parcourir.  
  
## <a name="SaveSession"></a>Enregistrement des données IntelliTrace dans un fichier  
 Vous pouvez enregistrer les données recueillies par IntelliTrace en accédant à **Déboguer / IntelliTrace / Enregistrer la session IntelliTrace** pendant que vous déboguez et que l'application est dans un état d'arrêt. L'élément de menu est désactivé et vous ne pourrez pas enregistrer les données recueillies par IntelliTrace si l'application est encore en cours d'exécution ou si vous avez arrêté le débogage.  
  
 Vous pouvez configurer IntelliTrace pour enregistrer automatiquement les données dans un fichier en accédant à **Outils / Options / IntelliTrace / Avancé** et en sélectionnant **Stocker les enregistrements IntelliTrace dans ce répertoire**. Vous pouvez aussi configurer une taille fixe pour le fichier généré. Dans ce cas, IntelliTrace remplace les anciennes données quand l'espace libre est insuffisant. Visual Studio crée deux fichiers pour chaque session IntelliTrace quand elles sont enregistrées automatiquement et que le processus d'hébergement Visual Studio (vshost.exe) est activé.  
  
> [!TIP]
> Pour économiser de l'espace disque, désactivez l'enregistrement automatique des fichiers quand vous n'en avez plus besoin. Les fichiers existants ne seront pas supprimés. Vous pouvez toujours enregistrer les données dans un fichier à la demande à partir du menu contextuel.  
  
 Quand vous enregistrez des données IntelliTrace dans un fichier, vous obtenez un fichier .itrace pour chaque processus à partir duquel IntelliTrace a recueilli des données. Vous pouvez ensuite ouvrir le fichier .itrace dans Visual Studio en accédant à **Fichier / Ouvrir / Fichier** et en sélectionnant le fichier .itrace dans la boîte de dialogue Ouvrir un fichier. Pour plus d’informations, consultez [Utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md).  
  
## <a name="blogs"></a>Blogs  
 [IntelliTrace dans Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)  
  
 [Procédure pas à pas de débogage en direct à l’aide d’IntelliTrace dans Visual Studio 2015 (éditeur de texte)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)  
  
 [Procédure pas à pas de débogage en direct à l’aide d’IntelliTrace dans Visual Studio 2015 (Club social)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)  
  
 [IntelliTrace dans Visual Studio Enterprise 2015 prend désormais en charge Attach !](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)  
  
 [Collecter des données à partir d’un service Windows à l’aide du collecteur autonome IntelliTrace](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)  
  
 [Modification du plan de collecte IntelliTrace](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan/)  
  
 [TraceSource personnalisé et débogage à l’aide d’IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)  
  
 [Collecteur autonome IntelliTrace et pools d’applications s’exécutant sous des comptes Active Directory](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)  
  
## <a name="forums"></a>Forums  
 [Débogueur Visual Studio](https://go.microsoft.com/fwlink/?LinkId=262263)  
  
## <a name="videos"></a>Vidéos  
 [Expérience IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)

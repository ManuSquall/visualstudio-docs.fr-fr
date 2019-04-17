---
title: Guide pratique pour signaler un problème avec Visual Studio
description: Découvrez comment signaler un problème avec Visual Studio.
ms.date: 03/11/2018
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
ms.author: seiyer
author: seaniyer
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b130c321e57cdeea6b703b0e439d6b0f15a1a96
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232539"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Guide pratique pour signaler un problème avec Visual Studio ou Visual Studio Installer

> [!NOTE]
> Pour Visual Studio pour Mac, consultez [Guide pratique pour signaler un problème dans Visual Studio pour Mac](/visualstudio/mac/report-a-problem).

Il est possible de signaler un problème dans Visual Studio ou dans son programme d’installation à l’aide de l’outil Feedback Tool inclus. Ce dernier vous permet d’inclure facilement des informations de diagnostic dans vos commentaires et aide les équipes de Visual Studio à diagnostiquer et à résoudre les problèmes beaucoup plus efficacement. Voici les étapes à suivre pour signaler un problème.

1. **Dans Visual Studio**, sélectionnez l’icône de commentaires en haut à droite et sélectionnez Signaler un problème. Feedback Tool est également accessible dans le menu **Aide** > **Envoyer des commentaires** > **Signaler un problème**.
![Fenêtre contextuelle Signaler un problème sur la communauté des développeurs Visual Studio](media/vsfeedbackentry.png) Si vous ne parvenez pas à installer Visual Studio ou à accéder à Feedback Tool dans Visual Studio, signalez un problème dans **Visual Studio Installer**.  Dans le programme d’installation, sélectionnez l’icône de commentaires en haut à droite, puis Signaler un problème.
![Fenêtre contextuelle de signalement de problème sur le site web de la Communauté des développeurs Visual Studio](media/installer.png)

1. Si ce n’est pas déjà fait, sélectionnez **Se connecter** comme sur la capture d’écran suivante. Suivez les instructions à l’écran pour vous connecter.

   ![Se connecter pour signaler un problème](../ide/media/sign-in-new-ux.png)

   Une fois votre session ouverte, vous pouvez non seulement signaler un problème, mais aussi voter et commenter les retours d’expérience existants.

1. Vos **Problèmes** et votre **Activité** apparaissent sur l’écran **Éléments suivis**.

   ![Éléments suivis](../ide/media/items-i-follow.png)

1. Visual Studio fournit une interface pour rechercher votre problème et voir si d’autres personnes l’ont signalé. S’il a déjà été signalé par quelqu’un d’autre, rappelez-le nous en votant.
   > [!NOTE]
   > Pour effectuer une recherche, entrez le texte souhaité dans la zone de recherche et cliquez sur Entrée ou appuyez sur l’icône Rechercher.

   ![Rechercher et voter pour des problèmes similaires](../ide/media/search-and-vote.png)

1. Si vous ne trouvez pas le problème rencontré, choisissez **Signaler un nouveau problème** en bas de l’écran.

   > [!NOTE]
   > Le bouton **Signaler un nouveau problème** apparaît uniquement dans l’interface de Visual Studio pour la Communauté des développeurs. Vous ne pouvez pas signaler un problème directement sur le site web de la [Communauté des développeurs](https://developercommunity.visualstudio.com/).

1. Créez un titre descriptif pour le problème, qui nous permet de l’adresser à l’équipe Visual Studio appropriée.

1. Donnez-nous des détails supplémentaires et, si possible, indiquez-nous les étapes de reproduction du problème.

   ![Signaler un nouveau problème](../ide/media/report-new-problem.png)

1. Sélectionnez **Suivant** pour accéder à l’onglet **Pièces jointes**. Ici, vous pouvez effectuer une capture d’écran pour l’envoyer à Microsoft. Pour joindre d’autres captures d’écran ou d’autres fichiers, choisissez **Joindre des fichiers supplémentaires**.

   ![Joindre une capture d’écran à un rapport de problème Visual Studio](media/report-a-problem-screenshot.png)

1. Si vous ne souhaitez pas joindre de capture d’écran ou [enregistrer une reproduction](#record-a-repro), sélectionnez **Suivant** pour accéder à l’onglet **Résumé**.

1. Sélectionnez **Envoyer** pour envoyer votre rapport, ainsi que les images et fichiers d’image mémoire de tas ou de trace. (Si le bouton **Envoyer** est grisé, vérifiez que vous avez fourni un titre et une description pour le rapport.)

   Pour plus d’informations sur les données collectées, consultez [Données que nous collectons](developer-community-privacy.md#data-we-collect).

## <a name="record-a-repro"></a>Enregistrer une reproduction

Les fichiers heap dump et de trace nous sont utiles pour faciliter le diagnostic des problèmes. Nous vous remercions d’employer l’outil **Signaler un problème** pour enregistrer les étapes de reproduction de votre problème et envoyer les données à Microsoft. Voici comment faire :

1. Après avoir entré un titre et une description pour votre problème, sélectionnez **Suivant** afin d’accéder à l’onglet **Pièces jointes**.

1. Sélectionnez l’onglet **Enregistrer**.

1. Sous **Enregistrer vos actions**, sélectionnez l’instance actuelle de Visual Studio si vous pouvez y reproduire le problème. Si vous ne le pouvez pas, par exemple si Visual Studio ne répond pas, sélectionnez **\<Créer une instance>** pour enregistrer les actions dans une nouvelle instance de Visual Studio.

1. Sélectionnez **Démarrer l’enregistrement**. Accordez l’autorisation d’exécuter l’outil.

   ![Choisissez « Démarrer l’enregistrement » pour fournir un fichier d’image mémoire de tas et de trace dans un rapport de problème Visual Studio.](../ide/media/record-dialog-box.png)

1. Quand l’outil **Enregistreur d’actions utilisateur** apparaît, effectuez les étapes qui reproduisent le problème.

1. Quand vous avez terminé, choisissez le bouton **Arrêter l’enregistrement**.

1. Attendez quelques minutes que Visual Studio collecte et compresse les informations que vous avez enregistrées.

   Pour plus d’informations sur les données collectées, consultez [Données que nous collectons](developer-community-privacy.md#data-we-collect).

## <a name="when-further-information-is-needed-need-more-info"></a>Quand d’autres informations sont nécessaires (Besoin de plus d’informations)

À compter de Visual Studio 2017 version 15.5, il existe un nouveau flux de travail pour aider les utilisateurs à fournir des informations supplémentaires sur les rapports de problème.

1. Quand un ingénieur Microsoft définit le problème de la [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/) à l’état **Besoin de plus d’informations**, tout utilisateur ayant voté, suivi ou commenté le problème reçoit une notification dans l’outil **Signaler un problème** dans Visual Studio.

   ![Notification « Besoin de plus d’informations » dans Visual Studio](../ide/media/nmi-notification.png)

1. Cliquez sur le lien **Afficher les problèmes** pour filtrer et trier la vue avec les problèmes nécessitant votre attention. Un indicateur figure également en regard de ces problèmes, afin de les différencier dans la recherche générale.

1. Cliquez sur un problème pour en afficher les détails.

   ![Notification « Besoin de plus d’informations »](../ide/media/nmi-details-view.png)

1. Pour afficher la demande **Besoin de plus d’informations**, cliquez sur le lien **Afficher leurs demandes et y répondre** dans la vue de détails du problème. Une boîte de dialogue montre la demande.

   ![Notification « Besoin de plus d’informations »](../ide/media/nmi-request.png)

1. Vous pouvez fournir plus d’informations en ajoutant des commentaires ou des pièces jointes, ou en enregistrant des étapes. Cette expérience est similaire au signalement d’un nouveau problème ou à l’apport d’informations supplémentaires lors du vote sur un problème.

1. L’ingénieur Microsoft reçoit une notification concernant les informations supplémentaires fournies. S’il dispose de suffisamment d’informations pour étudier le problème, l’état du problème change. Sinon, l’ingénieur demande encore plus d’informations.

   > [!NOTE]
   > * Quand vous répondez, la notification disparaît. À la place apparaît une bannière qui vous remercie et permet de fournir encore plus d’informations.
   > * Une fois que l’état du problème a changé, la notification disparaît pour tous les utilisateurs qui suivent le problème.
   > * Plusieurs personnes peuvent répondre à la même demande **Besoin de plus d’informations**.
   > * Il n’existe pas de flux de travail **Besoin de plus d’informations** sur le site web de la [Communauté des développeurs](https://developercommunity.visualstudio.com/) quand vous y accédez directement par le biais d’un navigateur web, mais vous pouvez également y ajouter des commentaires et des pièces jointes.

## <a name="search-for-solutions-or-provide-feedback"></a>Rechercher des solutions ou fournir des commentaires

Si vous ne souhaitez pas ou ne pouvez pas utiliser Visual Studio pour signaler un problème, il est possible que ce dernier ait déjà été signalé et qu’une solution ait été publiée sur la page de la [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/).

Si vous n’avez pas de problème à signaler, mais que vous voulez suggérer une fonctionnalité, il existe pour cela un emplacement spécifique. Pour plus d’informations, consultez la page [Suggérer une fonctionnalité](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="see-also"></a>Voir aussi

* [Nous contacter](../ide/talk-to-us.md)
* [Signaler un problème avec Visual Studio pour Mac](/visualstudio/mac/report-a-problem)
* [Signaler un problème avec C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/)
* [Confidentialité des données de la communauté des développeurs](developer-community-privacy.md)

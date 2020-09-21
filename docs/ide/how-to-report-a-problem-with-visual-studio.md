---
title: Guide pratique pour signaler un problème avec Visual Studio
description: Découvrez comment signaler un problème avec Visual Studio.
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2deb3f8ff19c2d7805031c0c3ba02bc82b8a3e7
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810872"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Guide pratique pour signaler un problème avec Visual Studio ou Visual Studio Installer

> [!NOTE]
> Pour Visual Studio pour Mac, consultez [Guide pratique pour signaler un problème dans Visual Studio pour Mac](/visualstudio/mac/report-a-problem).

Vous pouvez signaler un problème à partir de Visual Studio ou de son programme d’installation. L’outil de commentaires intégré vous permet d’ajouter facilement des informations de diagnostic qui aident les équipes Visual Studio à diagnostiquer et à résoudre les problèmes. Voici les étapes à suivre pour signaler un problème.

1. **Dans Visual Studio**, sélectionnez l’icône de commentaires en haut à droite et sélectionnez Signaler un problème. Vous pouvez également accéder à l’outil commentaires à partir du menu **aide**  >  **Envoyer des commentaires**  >  **signaler un problème**.
![Signalez un problème lié à la communauté de développeurs Visual Studio ](media/feedback-button.png) . vous pouvez également signaler un problème dans **Visual Studio installer** si vous ne pouvez pas installer Visual Studio ou si vous ne parvenez pas à accéder à l’outil commentaires dans Visual Studio.  Dans le programme d’installation, sélectionnez l’icône de commentaires en haut à droite, puis Signaler un problème.
![Fenêtre contextuelle Signaler un problème sur la communauté des développeurs Visual Studio](media/installer.png)

1. En cliquant sur **signaler un problème** , vous ouvrez votre navigateur par défaut et vous vous connectez à l’aide du même compte que celui utilisé pour vous connecter à Visual Studio.

   ![Se connecter pour signaler un problème](../ide/media/feedback-browser-top.png)

1. Commencez par entrer le titre descriptif de votre rapport de bogue. Il doit comporter au moins 25 caractères.

    ![Signaler un problème](../ide/media/feedback-report.png)

1. Une fois que vous commencez à taper, les doublons possibles sont affichés sous le champ titre

    ![Rechercher les doublons](../ide/media/feedback-search.png)

1. Sélectionnez les rapports de bogues qui peuvent être dupliqués pour voir si l’un d’eux correspond à votre propre problème. Si c’est le cas, votez pour lui au lieu de créer votre propre ticket.

    ![Vote pour les doublons](../ide/media/feedback-duplicate.png)

2. Si aucun doublon n’a été trouvé, continuez en entrant une description du problème. Il est important d’être aussi clair que possible pour augmenter les chances d’être en mesure de reproduire le bogue. Veillez à inclure des étapes de reproduction claires.

3. Si cela s’applique au rapport de bogue, prenez une capture d’écran en cochant la case *inclure la capture d’écran de Visual Studio* .

    ![Prenez une capture d’écran ](../ide/media/feedback-screenshot.png) *seuls les ingénieurs Microsoft peuvent voir la capture d’écran*

    Vous pouvez même rogner la capture d’écran directement dans le navigateur pour supprimer les parties sensibles ou non liées.

4. L’une des meilleures façons d’aider l’équipe d’ingénierie de Visual Studio à résoudre le problème, est de fournir un suivi et des fichiers de vidage du tas pour les examiner. Vous pouvez le faire facilement en enregistrant les étapes qui ont entraîné le bogue. 

    ![Enregistrer vos actions ](../ide/media/feedback-recording.png) *seuls les ingénieurs Microsoft peuvent voir l’enregistrement*

5. Passez en revue les fichiers joints et chargez les fichiers supplémentaires si vous pensez que cela peut vous aider à diagnostiquer le problème.   

    ![Fichiers joints ](../ide/media/feedback-attachments.png) *seuls les ingénieurs Microsoft peuvent voir les fichiers joints*

6. La dernière étape consiste à appuyer sur le bouton **Envoyer** . L’envoi du rapport l’enverra directement dans le système de rapports de bogues Visual Studio interne qui attend le triage.

## <a name="when-further-information-is-needed"></a>Quand des informations supplémentaires sont nécessaires

Lorsqu’il manque des informations importantes dans un problème, nous attribuons l’état **plus** d’informations. Nous nous penchons sur le problème avec les informations spécifiques dont nous avons besoin et vous recevrez une notification par courrier électronique. Si nous ne recevons pas les informations dans les sept jours, nous vous enverrons un rappel. Après cela, nous fermons le ticket au bout de 14 jours d’inactivité.

1. Suivez le lien du message électronique vers le rapport de problème ou accédez à mes commentaires pour voir tous les rapports dans l’état **needs more info** .

    ![Mes commentaires](../ide/media/feedback-my-feedback.png)

1. Si vous sélectionnez le lien fournir plus d’informations sur le rapport de problème, vous accédez à un nouvel écran. À partir de là, vous pouvez voir quelles sont les informations demandées.

   ![Mes commentaires](../ide/media/feedback-need-more-info.png)

1. Vous pouvez fournir plus d’informations en ajoutant des commentaires ou des pièces jointes, ou en enregistrant des étapes. Cette expérience est similaire au signalement d’un nouveau problème ou à l’apport d’informations supplémentaires lors du vote sur un problème.

1. L’ingénieur Microsoft reçoit une notification concernant les informations supplémentaires fournies. S’il dispose de suffisamment d’informations pour étudier le problème, l’état du problème change. Sinon, l’ingénieur demande encore plus d’informations.

Vous pouvez voir ces demandes sur l’écran **mes commentaires** , ainsi que tous les autres **problèmes** et **suggestions**.

## <a name="search-for-solutions-or-provide-feedback"></a>Rechercher des solutions ou fournir des commentaires

Si vous ne souhaitez pas ou ne pouvez pas utiliser Visual Studio pour signaler un problème, il est possible que ce dernier ait déjà été signalé et qu’une solution ait été publiée sur la page de la [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/).

Si vous n’avez pas de problème à signaler, mais que vous souhaitez suggérer une fonctionnalité, il existe un emplacement pour faire cela. Pour plus d’informations, consultez la page [Suggérer une fonctionnalité](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="see-also"></a>Voir aussi

* [Recommandations de la communauté des développeurs](./developer-community-guidelines.md)
* [Options de commentaires de Visual Studio](../ide/feedback-options.md)
* [Signaler un problème avec Visual Studio pour Mac](/visualstudio/mac/report-a-problem)
* [Signaler un problème avec C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/)
* [Confidentialité des données de la communauté des développeurs](developer-community-privacy.md)
---
title: Guide pratique pour signaler un problème avec Visual Studio 2017 | Microsoft Docs
ms.custom: ''
ms.date: 03/11/2018
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: TerryGLee
ms.author: tglee
manager: douge
ms.technology: vs-acquisition
ms.workload:
- multiple
ms.openlocfilehash: eacb6ba97f79f2c66444bc79b11c51ef01a50672
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-report-a-problem-with-visual-studio-2017"></a>Guide pratique pour signaler un problème avec Visual Studio 2017

Si vous rencontrez un problème avec Visual Studio, nous aimerions en être informés. Voici comment nous signaler le problème pour nous permettre de le diagnostiquer et le corriger.

## <a name="sign-in-to-visual-studio"></a>Se connecter à Visual Studio

Si ce n’est pas déjà fait, connectez-vous à Visual Studio avant de signaler un problème. De cette façon, non seulement vous pouvez signaler un problème auquel vous êtes confronté, mais vous pouvez aussi voter ou le commenter. Vous pouvez même ajouter un vote ou un commentaire pour des problèmes ayant été postés par d’autres utilisateurs.

1. Dans Visual Studio, sélectionnez **Aide** > **Envoyer des commentaires** > **Signaler un problème**.
2. Si vous n’avez pas ouvert de session, cliquez sur le bouton **Se connecter** situé sur le côté droit de l’outil, comme dans la capture d’écran suivante.
3. Suivez les instructions à l’écran pour vous connecter.

 ![Se connecter pour signaler un problème](../ide/media/sign-in-new-ux.png "Se connecter pour signaler un problème")  

## Rechercher et voter pour des problèmes similaires<a name="search_and_vote"></a>

1. Recherchez votre problème pour voir s’il a également été signalé par d’autres utilisateurs.
2. S’il a déjà été signalé par quelqu’un d’autre, rappelez-le nous en votant.

  ![Rechercher et voter pour des problèmes similaires](../ide/media/search-and-vote.png "Rechercher et voter pour des problèmes similaires")

## Signaler un nouveau problème<a name="report_new_problem"></a>

1. Si vous ne trouvez pas ce que vous recherchez, choisissez le bouton **Signaler un nouveau problème** en bas de l’écran.
2. Créez un titre descriptif pour le problème, qui nous permet de l’adresser à l’équipe Visual Studio appropriée.
3. Donnez-nous des détails supplémentaires et, si possible, indiquez-nous les étapes de reproduction du problème.

  ![Signaler un nouveau problème](../ide/media/report-new-problem.png "Signaler un nouveau problème")

## Fournir une capture d’écran et des pièces jointes (facultatif)<a name="provide_screenshots"></a>

 Choisissez d’envoyer votre écran actuel à Microsoft. Vous pouvez joindre d’autres captures d’écran ou fichiers en choisissant le bouton **Joindre des fichiers supplémentaires**.

## Fournir une trace et un heap dump (facultatif)<a name="provide_a_trace_and_heap_dump"></a>

Les fichiers heap dump et de trace nous sont utiles pour faciliter le diagnostic des problèmes. Nous vous remercions d’employer l’outil **Signaler un problème** pour enregistrer les étapes de reproduction de votre problème et envoyer les données à Microsoft. Voici comment faire.

1. Choisissez l’onglet **Enregistrer**.
2. Choisissez **Démarrer l’enregistrement**. Accordez l’autorisation d’exécuter l’outil.

  ![Choisissez Démarrer l’enregistrement pour fournir un fichier d’instantané du segment de mémoire et de trace ](../ide/media/record-dialog-box.png "Fournir un fichier d’instantané du segment de mémoire et de trace")

3. Quand l’outil **Enregistreur d’actions utilisateur** apparaît, effectuez les étapes qui reproduisent le problème.
4. Quand vous avez terminé, choisissez le bouton **Arrêter l’enregistrement**.
5. Attendez quelques minutes que Visual Studio collecte et compresse les informations que vous avez enregistrées.

## Envoyer le rapport<a name="submit_the_report"></a>

 Choisissez le bouton **Envoyer** pour envoyer votre rapport, ainsi que les images et les fichiers dump ou de trace. (Si le bouton **Envoyer** est grisé, vérifiez que vous avez fourni un titre et une description pour le rapport.)

## Autres méthodes de signalement <a name="alternate_reporting"></a>

### <a name="report-a-problem-by-using-the-visual-studio-installer"></a>Signaler un problème avec le programme d’installation de Visual Studio

Si vous ne parvenez pas à installer Visual Studio, ou si vous ne pouvez pas accéder à l’outil Commentaires dans Visual Studio, vous pouvez signaler un problème à l’aide de **Visual Studio Installer**. Pour ce faire, choisissez l’icône Commentaires dans le coin supérieur droit de **Visual Studio Installer**.

 ![Utilisez la touche Tab pour accéder au bouton Fournir des commentaires dans Visual Studio Installer et ouvrir Feedback Tool](../install/media/report-a-problem.png)

### <a name="search-for-problems-and-solutions-by-using-the-visual-studio-developer-community"></a>Rechercher des solutions aux problèmes sur Visual Studio Developer Community

Si vous ne souhaitez pas ou ne pouvez pas utiliser Visual Studio pour signaler un problème, il est possible que ce dernier ait déjà été signalé et qu’une solution ait été postée sur le site Visual Studio Developer Community. Pour plus d’informations, consultez la page [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/).

#### <a name="provide-product-feedback-or-a-suggestion"></a>Fournir des commentaires ou une suggestion sur le produit

Si vous n’avez pas de problème à signaler mais que vous voulez faire des commentaires ou une suggestion, il existe pour cela un emplacement spécifique. Pour plus d’informations, consultez la page [UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-ide).

## <a name="see-also"></a>Voir aussi

* [Nous contacter](../ide/talk-to-us.md)
* [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/)

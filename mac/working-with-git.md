---
title: Utilisation de Git
description: Utilisation de Git dans Visual Studio pour Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: b047222f67d75bbc092a731c8de1ca1ba6d94cf7
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692165"
---
# <a name="working-with-git"></a>Utilisation de Git

Git est un système de gestion de versions distribué qui permet aux équipes de travailler simultanément sur les mêmes documents. Cela signifie qu’il existe un seul serveur contenant tous les fichiers, mais que quand un dépôt est extrait de cette source centrale, l’intégralité du dépôt est clonée sur la machine locale.

Dans les sections ci-dessous, nous allons examiner comment Git peut être utilisé pour la gestion de version dans Visual Studio pour Mac.

## <a name="git-version-control-menu"></a>Menu Gestion de version Git

L’image ci-dessous illustre les options fournies par Visual Studio pour Mac par l’élément de menu Gestion de version :

![Élément de menu Gestion de version](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Envoyer (push) et Tirer (pull)

L’envoi et le tirage sont les deux actions les plus souvent utilisées dans Git. Pour synchroniser les modifications que d’autres personnes ont apportées sur le dépôt distant, vous devez les **Tirer (pull)** du dépôt. Pour ce faire, dans Visual Studio pour Mac, sélectionnez **Gestion de version > Mettre à jour la solution**.

Une fois que vous avez mis à jour vos fichiers, que vous les avez examinés et validés, vous devez les **Envoyer (push)** dans le dépôt distant pour autoriser les autres utilisateurs à accéder à vos modifications. Pour ce faire, dans Visual Studio pour Mac, sélectionnez **Gestion de version > Envoyer (push) les modifications**. La boîte de dialogue Envoyer (push) s’affiche, dans laquelle vous pouvez voir les modifications validées et sélectionner la branche vers laquelle effectuer l’envoi :

![Boîte de dialogue affichant la branche vers laquelle envoyer les validations](media/version-control-gitPush.png)

Vous pouvez également Valider et Envoyer (push) vos modifications en même temps, via la boîte de dialogue Valider :

![Option montrant comment valider et envoyer (push) les modifications en même temps.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Responsable, Journal et Fusion

Au bas de la fenêtre, cinq onglets s’affichent, comme illustré ci-dessous :

![Onglets de la gestion de version](media/version-control-gitTabs.png)

Ces onglets permettent d’effectuer les actions suivantes :

* **Source** : Affiche votre fichier de code source.
* **Modifications** : Affiche la modification du code entre votre fichier local et le fichier de base. Vous pouvez également comparer différentes versions du fichier à partir de hachages différents :

    ![Onglet Modifications](media/version-control-gitChange.png)

* **Responsable** : Affiche le nom de l’utilisateur associé à chaque section de code.
* **Journal** : Affiche toutes les validations, heures, dates, messages et utilisateurs qui sont responsables du fichier :

    ![Onglet Journal](media/version-control-gitLog.png)

* **Fusion** : Cet onglet peut être utilisé en cas de conflit de fusion pendant la validation de votre travail. Il montre une représentation visuelle des modifications apportées par vous et l’autre développeur, ce qui vous permet de combiner correctement les deux sections de code.

## <a name="switching-branches"></a>Changement de branches

Par défaut, la première branche créée dans un dépôt est appelée branche **maîtresse** . Techniquement, il n’y a aucune différence entre la branche maître et les autres branches, si ce n’est que la branche maître est celle qui est le plus souvent considérée par les équipes de développeurs comme la branche « active » ou « de production ».

Une ligne indépendante de développement peut être créée en séparant la branche maître (ou n’importe quelle autre branche, dans notre exemple). Vous obtenez alors une nouvelle version de la branche maître à un point dans le temps, ce qui vous permet de séparer le développement de ce qui est « actif ». L’utilisation de branches de cette manière est souvent utilisée pour les fonctionnalités dans le cadre du développement de logiciels

Les utilisateurs peuvent créer autant de branches qu’ils le souhaitent pour chaque dépôt, mais il est recommandé de supprimer les branches après leur utilisation, pour que le dépôt reste organisé.

Les branches sont affichées dans Visual Studio pour Mac en accédant à **Gestion de version > Gérer les branches et les dépôts distants...**  :

![Affichage des branches](media/version-control-gitBranch2.png)

Passez d’une branche à l’autre en la sélectionnant dans la liste et en appuyant sur le bouton **Basculer vers la branche**.

Pour créer une branche, sélectionnez le bouton **Nouveau** dans la boîte de dialogue de configuration du dépôt Git. Entrez le nom de la nouvelle branche :

![Créer une branche](media/version-control-gitBranch.png)

Vous pouvez également définir une branche distante sur votre branche de _suivi_. Découvrez plus d’informations sur les branches de suivi dans la [documentation Git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Affichez la branche actuelle dans le panneau Solutions, à côté du nom de projet :

 ![Branche actuelle affichée dans le panneau Solutions](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Examen et validation

Pour examiner les modifications apportées aux fichiers, utilisez les onglets Modifications, Responsable, Journal et Fusion de chaque document, comme illustré dans cette rubrique.

Examinez toutes les modifications d’un projet en accédant à l’élément de menu **Gestion de version > Examiner la solution et valider** :

![Affichage de l’examen du code](media/version-control-gitReviewCommit.png)

Ce menu permet d’afficher toutes les modifications de chaque fichier d’un projet avec les options Restaurer, Créer un correctif ou Valider.

Pour valider un fichier dans le dépôt distant, appuyez sur **Valider**, entrez un message de validation, puis confirmez avec le bouton Valider :

![Validation d’un fichier](media/version-control-gitCommit.png)

Une fois que vous avez validé les modifications, envoyez-les (push) dans le dépôt distant pour permettre aux autres utilisateurs de les afficher.

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Voir aussi

* [Partager du code avec Visual Studio 2017 et Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017)
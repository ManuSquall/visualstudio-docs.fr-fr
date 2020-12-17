---
title: Utilisation de Git
description: Utilisation de Git dans Visual Studio pour Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: dc865ec593f53149d9c004f252015def32325d18
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616175"
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

Par défaut, la première branche créée dans un référentiel est appelée branche **principale** . Il n’y a techniquement aucune différence entre la branche principale et toute autre branche, mais la branche principale est celle qui est le plus souvent considérée comme la branche « en direct » ou « production » dans les équipes de développement.

Une ligne de développement indépendante peut être créée en branchant la branche principale (ou toute autre branche). Cela fournit une nouvelle version de la branche principale à un moment donné, ce qui permet un développement indépendant de ce qui est « en direct ». L’utilisation de branches de cette manière est souvent utilisée pour les fonctionnalités dans le cadre du développement de logiciels

Les utilisateurs peuvent créer autant de branches qu’ils le souhaitent pour chaque dépôt, mais il est recommandé de supprimer les branches après leur utilisation, pour que le dépôt reste organisé.

Les branches sont affichées dans Visual Studio pour Mac en accédant à **Gestion de version > Gérer les branches et les dépôts distants...**  :

![Affichage des branches](media/version-control-gitBranch2.png)

Passez d’une branche à l’autre en la sélectionnant dans la liste et en appuyant sur le bouton **Basculer vers la branche**.

Pour créer une branche, sélectionnez le bouton **Nouveau** dans la boîte de dialogue de configuration du dépôt Git. Entrez le nom de la nouvelle branche :

![Créer une branche](media/version-control-gitBranch.png)

Vous pouvez également définir une branche distante sur votre branche de _suivi_. Découvrez plus d’informations sur les branches de suivi dans la [documentation Git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Consultez la branche Current Branch dans la fenêtre de la solution, en regard du nom du projet :

 ![Branche actuelle affichée dans la fenêtre de la solution](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Examen et validation

Pour examiner les modifications apportées aux fichiers, utilisez les onglets Modifications, Responsable, Journal et Fusion de chaque document, comme illustré dans cette rubrique.

Examinez toutes les modifications d’un projet en accédant à l’élément de menu **Gestion de version > Examiner la solution et valider** :

![Affichage de l’examen du code](media/version-control-gitReviewCommit.png)

Ce menu permet d’afficher toutes les modifications de chaque fichier d’un projet avec les options Restaurer, Créer un correctif ou Valider.

Pour valider un fichier dans le référentiel distant, appuyez sur **valider**, entrez un message de validation et confirmez avec le bouton valider :

![Validation d’un fichier](media/version-control-gitCommit.png)

Une fois que vous avez validé les modifications, envoyez-les (push) dans le dépôt distant pour permettre aux autres utilisateurs de les afficher.

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Voir aussi

* [Partager du code avec Visual Studio 2017 et Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017)

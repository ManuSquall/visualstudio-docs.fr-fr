---
title: TF Version Control
description: Connexion à Team Foundation Server ou Visual Studio Team Services avec Team Foundation Version Control.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: f892209faeb06ca703d28016457e9ba4ab86ccda
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="connecting-to-team-foundation-version-control"></a>Connexion à Team Foundation Version Control 

VSTS (Visual Studio Team Services) et TFS (Team Foundation Server) fournissent deux modèles de gestion de versions : Git, qui est un modèle distribué, et TFVC (Team Foundation Version Control), qui est un modèle centralisé. Cet article fournit une vue d’ensemble de Team Foundation Version Control et décrit les premiers pas à suivre pour l’utiliser avec Visual Studio pour Mac.

> [!NOTE]
> **Remarque** : La prise en charge de Team Foundation Version Control est actuellement en préversion, et il est possible que certaines fonctionnalités ne soient pas encore entièrement opérationnelles. D’autres changements sont prévus !

## <a name="requirements"></a>Configuration requise

* Visual Studio pour Mac version 7.5 ou ultérieure
* Visual Studio Team Servers ou Team Foundation Server 2013 et ultérieur
* Un projet dans Visual Studio Team Services ou Team Foundation Server configuré pour utiliser Team Foundation Version Control.

## <a name="installation"></a>Installation

Dans Visual Studio pour Mac, choisissez le menu **Visual Studio > Extensions**. Recherchez « TF version control » et installez l’extension **Team Foundation Version Control**. Redémarrez l’IDE quand vous y êtes invité.

## <a name="using-the-add-in"></a>Utilisation du complément

Une fois l’extension installée, sélectionnez le menu **Gestion de version > TFS/VSTS > Se connecter à Team Foundation Version Control**. 

![Ajouter un serveur TFVC](media/tfvc-add-remove-server.png)


Choisissez Visual Studio Team Services ou Team Foundation Server pour démarrer :

![Se connecter avec un serveur TFVC](media/tfvc-choose-server-type.png)

Entrez vos informations d’identification : 

![Se connecter à un serveur TFVC](media/tfvc-login.png)

Choisissez ensuite les projets auxquels vous souhaitez accéder : 

![Choisir des projets](media/tfvc-choose-projects.png)

Pour continuer, fermez les boîtes de dialogue, puis utilisez le menu **Gestion de version > TFS/VSTS > Explorateur du contrôle de code source** pour parcourir la source.

> [!WARNING]
> **Problème connu** : Dans cette préversion, vous devrez créer un espace de travail la première fois que vous ouvrez l’Explorateur du contrôle de code source.

![Explorateur de la source](media/tfvc-source-explorer.png)

Dans l’Explorateur du contrôle de code source, vous pouvez parcourir votre code source sur le serveur et effectuer les actions suivantes :

- Gérer des espaces de travail (créer, modifier ou supprimer)
- Naviguer dans la structure du projet
- Mapper des projets
- Obtenir des projets
- Verrouiller et déverrouiller des fichiers
- Renommer des fichiers
- Supprimer des fichiers
- Ajouter un nouveau fichier
- Extraire
- Archiver
- Afficher les changements d’historique
- Comparer les changements

## <a name="creating-a-new-workspace"></a>Créer un espace de travail

Dans l’Explorateur du contrôle de code source, cliquez sur le bouton **Gérer les espaces de travail**. 

![Gérer les espaces de travail](media/tfvc-manage-workspaces.png)

Cliquez sur **Ajouter** pour créer un espace de travail.

![Créer un espace de travail](media/tfvc-create-workspace.png)

Nommez l’espace de travail, puis cliquez sur **Ajouter un dossier de travail** pour mapper le projet à un dossier local sur votre ordinateur.

Une fois terminé, cliquez sur **OK**, puis fermez la boîte de dialogue Gérer les espaces de travail. Vous pouvez alors obtenir les fichiers par le biais de l’Explorateur du contrôle de code source et démarrer.
---
title: TF Version Control
description: Connexion à Team Foundation Server ou Visual Studio Team Services avec Team Foundation Version Control.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 58d0fc5c31b02574661f8b86a4ae8bcaf393be3a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693771"
---
# <a name="connecting-to-team-foundation-version-control"></a>Connexion à Team Foundation Version Control 

> [!NOTE]
> **Remarque** : La prise en charge de Team Foundation Version Control est actuellement en préversion, et il est possible que certaines fonctionnalités ne soient pas encore entièrement opérationnelles. Nous aimerions beaucoup recevoir vos commentaires sur [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) concernant les problèmes que vous rencontrez. D’autres changements sont prévus !

VSTS (Visual Studio Team Services) et TFS (Team Foundation Server) fournissent deux modèles de gestion de versions : Git, qui est un modèle distribué, et TFVC (Team Foundation Version Control), qui est un modèle centralisé. Cet article fournit une vue d’ensemble de Team Foundation Version Control et décrit les premiers pas à suivre pour l’utiliser avec Visual Studio pour Mac.

## <a name="requirements"></a>Configuration requise

* Visual Studio pour Mac version 7.5 ou ultérieure
* Visual Studio Team Services ou Team Foundation Server 2013 et ultérieur
* Un projet dans Visual Studio Team Services ou Team Foundation Server configuré pour utiliser Team Foundation Version Control.

## <a name="installation"></a>Installation

Dans Visual Studio pour Mac, choisissez **Visual Studio > Extensions...** dans le menu. Sous l’onglet **Galerie**, sélectionnez **Gestion de version > Team Foundation Version Control pour TFS et VSTS** et cliquez sur **Installer...**  :

  ![Gestionnaire d’extensions](media/tfvc-install.png) 

Suivez les invites pour installer l’extension. Une fois qu’elle est installée, redémarrez l’IDE.

## <a name="using-the-add-in"></a>Utilisation du complément

Une fois l’extension installée, sélectionnez l’élément de menu **Gestion de version > TFS/VSTS > Se connecter à Team Foundation Version Control**. Cliquez sur **Ajouter** pour ajouter un nouveau compte : 

![Ajouter un serveur TFVC](media/tfvc-add-remove-server.png)

Choisissez Visual Studio Team Services ou Team Foundation Server pour démarrer :

![Se connecter avec un serveur TFVC](media/tfvc-choose-server-type.png)

Entrez vos informations d’identification et cliquez sur **Se connecter** : 

![Se connecter à un serveur TFVC](media/tfvc-login.png)

Une fois que vous êtes connecté, sélectionnez les projets auxquels vous souhaitez accéder et appuyez sur **OK** : 

![Choisir des projets](media/tfvc-choose-projects.png)

Sélectionnez l’élément de menu **Gestion de version > TFS/VSTS > Explorateur du contrôle de code Source** pour ouvrir l’Explorateur du contrôle de code source qui vous permet d’accéder à la source.

> [!IMPORTANT]
> **Problème connu** : Dans cette préversion, vous devrez [créer un espace de travail](#creating-a-new-workspace) la première fois que vous ouvrez l’Explorateur du contrôle de code source.

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

Cliquez sur le bouton **Ajouter** pour créer un nouvel espace de travail.

![Créer un espace de travail](media/tfvc-create-workspace.png)

Nommez l’espace de travail, puis cliquez sur **Ajouter un dossier de travail** pour mapper le projet à un dossier local sur votre ordinateur.

Une fois terminé, cliquez sur **OK**, puis fermez la boîte de dialogue Gérer les espaces de travail. Vous pouvez alors obtenir les fichiers par le biais de l’Explorateur du contrôle de code source et démarrer.

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="problems-using-basic-authentication"></a>Problèmes avec l’authentification de base

Il existe différentes options disponibles pour procéder à l’authentification avec un serveur :

- Oauth
- De base
- Ntlm

Pour pouvoir utiliser l’authentification de base, il est nécessaire d’activer **Informations d’identification d’authentification alternatives** dans VSTS, en suivant les étapes ci-dessous :

1. Connectez-vous en tant que propriétaire du compte à votre compte VSTS (https://{youraccount}.visualstudio.com).
2. Dans la barre d’outils de votre compte, sélectionnez l’icône d’engrenage et sélectionnez **Stratégie** : ![Option de paramètres de stratégie sélectionnée](media/tfvc-auth2.png) 
3. Passez en revue les paramètres de connexion de votre application. Changez ces paramètres en fonction de vos stratégies de sécurité : ![Option de paramètres de stratégie sélectionnée](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>Je ne vois rien dans TFVC

Pour définir Team Foundation Version Control (TFVC) sur votre ordinateur de développement, vous **devez** créer un espace de travail, comme décrit dans la section [Création d’un espace de travail](#creating-a-new-workspace).

Dans l’Explorateur du contrôle de code source, appuyez sur le bouton **Gérer les espaces de travail**. Suivez les étapes pour mapper le projet d’équipe à un dossier de votre ordinateur de développement.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Je ne vois aucun de mes projets ou je ne les vois pas tous

Une fois l’authentification terminée, vous devriez voir la liste des projets. Par défaut, seuls les projets TFS sont affichés. Pour voir d’autres types de projets, cochez la case « Afficher tous les projets ».

N’oubliez pas que les projets qui se trouvent sur le serveur ne sont pas affichés si vous n’avez pas les privilèges appropriés.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>J’obtiens l’erreur « Impossible de créer l’espace de travail ». Veuillez réessayer. »

Quand vous tentez de [créer un espace de travail](#creating-a-new-workspace), vous devez vous assurer que les conditions suivantes sont remplies :

- Aucun caractère non valide dans le nom de l’espace de travail.
- Le nom doit comprendre moins de 64 caractères.
- Le chemin local ne peut pas être utilisé par d’autres espaces de travail.
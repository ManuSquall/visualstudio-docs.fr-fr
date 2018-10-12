---
title: Team Foundation Version Control (TFVC)
description: Connexion à Team Foundation Server ou à Azure DevOps Services avec Team Foundation Version Control (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 09/05/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 5a1d7fb7519e9402e2fa780e978fc1176702b26d
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542432"
---
# <a name="connecting-to-team-foundation-version-control"></a>Connexion à Team Foundation Version Control

> [!NOTE]
> **Remarque** : La prise en charge de Team Foundation Version Control est actuellement en préversion, et il est possible que certaines fonctionnalités ne soient pas encore entièrement opérationnelles. Nous aimerions beaucoup recevoir vos commentaires sur [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) concernant les problèmes que vous rencontrez. D’autres changements sont prévus !

Azure Repos fournit deux modèles de gestion de versions : Git, qui est un modèle distribué, et TFVC (Team Foundation Version Control), qui est un modèle centralisé. Cet article fournit une vue d’ensemble de TFVC et décrit les premiers pas à effectuer pour l’utiliser avec Visual Studio pour Mac.

## <a name="requirements"></a>Configuration requise

* Visual Studio Community, Professional ou Enterprise pour Mac version 7.5 ou ultérieure.
* Azure DevOps Services, ou Team Foundation Server 2013 et ultérieur.
* Un projet dans Azure DevOps Services ou Team Foundation Server, configuré pour utiliser Team Foundation Version Control.

## <a name="installation"></a>Installation

Dans Visual Studio pour Mac, choisissez **Visual Studio > Extensions...** dans le menu. Sous l’onglet **Galerie**, sélectionnez **Gestion de version > Team Foundation Version Control pour TFS et VSTS** et cliquez sur **Installer...**  :

  ![Gestionnaire d’extensions](media/tfvc-install.png)

Suivez les invites pour installer l’extension. Une fois qu’elle est installée, redémarrez l’IDE.

## <a name="updating-the-extension"></a>Mise à jour de l’extension

Les mises à jour de l’extension TFVC sont effectuées régulièrement. Pour accéder aux mises à jour, choisissez **Visual Studio > Extensions...** dans le menu et sélectionnez l’onglet **Mises à jour**. Sélectionnez l’extension dans la liste et appuyez sur le bouton **Mettre à jour** :

  ![Gestionnaire d’extensions indiquant la mise à jour](media/tfvc-update.png)

Appuyez sur **Installer** dans la boîte de dialogue suivante pour désinstaller l’ancien package et installer le nouveau.

Pour plus d’informations sur les nouveautés de chaque version, consultez les [Notes de publication](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-mac-preview-relnotes#team-foundation-version-control-extension--release-notes).

## <a name="using-the-add-in"></a>Utilisation du complément

Une fois l’extension installée, sélectionnez l’élément de menu **Gestion de version > TFS/Azure DevOps > Ouvrir à partir du dépôt distant**.

  ![Élément de menu pour ouvrir l’extension](media/tfvc-source-control-explorer-devops.png)

Choisissez VSTS ou Team Foundation Server pour démarrer, puis appuyez sur **Continuer** :

  ![Se connecter avec un serveur](media/tfvc-choose-server-type-devops.png)

### <a name="azure-repos-authentication"></a>Authentification d’Azure Repos

Quand vous sélectionnez un projet qui est hébergé dans Azure Repos, vous êtes invité à entrer les informations de votre compte Microsoft :

  ![Se connecter avec Azure Repos](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>Authentification TFS

Pour vous connecter à TFS, entrez les détails du serveur et les informations d’identification de votre compte. Entrez un domaine pour utiliser l’authentification NTLM, sinon laissez vide pour utiliser l’authentification de base. Sélectionnez **Ajouter un serveur** :

![Se connecter à un serveur TFS](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Sélection d’un projet

Une fois authentifié, vous pouvez voir une liste des dépôts qui sont associés à un compte dans la boîte de dialogue **Ouvrir depuis le contrôle de code source** :

  ![Boîte de dialogue Ouvrir depuis le contrôle de code source avec affichage des projets](media/tfvc-vsts-projects.png)

Cette boîte de dialogue est organisée avec les nœuds suivants :

- Organisation ou collection Azure DevOps : cette option affiche toutes les organisations connectées au compte Microsoft avec lequel vous avez ouvert une session.
- Projets : dans chaque organisation ou collection, vous pouvez avoir plusieurs projets. Un projet est l’endroit où sont hébergés le code source, les éléments de travail et les builds automatisées.

À ce stade, vous pouvez effectuer une recherche et filtrer par nom de projet ou par organisation.

### <a name="adding-a-new-server"></a>Ajout d’un nouveau serveur

Pour ajouter un nouveau serveur à la liste, appuyez sur le bouton **Ajouter un hôte** dans la boîte de dialogue **Ouvrir depuis le contrôle de code source** :

![Mise en valeur du bouton d’ajout permettant d’ajouter un nouveau serveur à la liste](media/tfvc-add-new-server.png)

Sélectionnez le fournisseur dans la liste, puis entrez vos informations d’identification :

![Boîte de dialogue affichant l’option du fournisseur de contrôle de code source](media/tfvc-add-new-creds-devops.png)

## <a name="creating-a-new-workspace"></a>Créer un espace de travail

Pour commencer à utiliser un projet, vous devez disposer d’un _espace de travail_. Si vous ne disposez pas d’un espace de travail, vous pouvez en créer un à partir de la zone de liste déroulante **Espace de travail** dans la boîte de dialogue **Ouvrir depuis le contrôle de code source** :

![Option de zone de liste déroulante permettant de créer un espace de travail](media/tfvc-create-new-workspace.png)

Définissez le nom et le chemin local de votre nouvel espace de travail et sélectionnez **Créer l’espace de travail** :

![Saisie du nom et du chemin local du nouvel espace de travail](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Utilisation de l’Explorateur du contrôle de code source

Après avoir créé un espace de travail et mappé votre projet, vous pouvez commencer à utiliser _l’Explorateur du contrôle de code source_.

Pour ouvrir l’Explorateur du contrôle de code source, sélectionnez l’élément de menu **Gestion de version > TFS/Azure DevOps > Explorateur du contrôle de code source**.

L’Explorateur du contrôle de code source vous permet de naviguer dans tous les projets mappés, leurs fichiers et dossiers. Il vous permet également d’effectuer toutes les actions de contrôle de code source de base telles que les suivantes :

- Obtenir la dernière version
- Obtenir une version spécifique
- Archiver et extraire des fichiers
- Verrouiller et déverrouiller des fichiers
- Ajouter, supprimer et renommer des fichiers
- Afficher l'historique
- Comparer les changements

Nombre de ces actions sont réalisables par le biais d’actions contextuelles sur le projet :

![Actions de menu contextuel pour un projet](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>Gestion des espaces de travail

Si vous n’avez pas déjà créé un espace de travail comme décrit dans la section [Création d’un espace de travail](#creating-a-new-workspace), vous pouvez remarquer que l’Explorateur de code source est vide :

![Explorateur de code source vide](media/tfvc-setup-empty-sce.png)

Pour configurer votre projet distant avec un espace de travail local, effectuez les étapes suivantes :

1. Sélectionnez le **Serveur** à partir de la zone de liste déroulante.
1. Notez qu’il n’y a « aucun espace de travail » et que le chemin local est « Non mappé ». Sélectionnez le lien **Non mappé** pour afficher la boîte de dialogue **Créer un espace de travail**.
1. Nommez l’espace de travail, puis cliquez sur **Ajouter un dossier de travail** pour mapper le projet à un dossier local sur votre ordinateur :

    ![Boîte de dialogue Créer un espace de travail montrant les options par défaut](media/tfvc-workspace1.png)

1. Sélectionnez le dossier « $ » pour mapper tous les projets sur votre serveur au même espace de travail, ou sélectionnez un projet individuel, puis cliquez sur **OK** :

    ![Boîte de dialogue Rechercher un dossier montrant tous les projets](media/tfvc-workspace2.png)

1. Sélectionnez l’emplacement sur votre ordinateur local auquel vous voulez mapper les projets, puis cliquez sur **Sélectionner un dossier**.
1. Vérifiez les détails du nouvel espace de travail en appuyant sur **OK**.

    ![Boîte de dialogue Créer un espace de travail montrant le dossier de travail ajouté](media/tfvc-workspace3.png)

Une fois votre espace de travail configuré, vous pouvez le changer ou le supprimer en cliquant sur le bouton **Gérer les espaces de travail** dans l’Explorateur du contrôle de code source.

![Gérer les espaces de travail](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="problems-using-basic-authentication"></a>Problèmes avec l’authentification de base

Vous pouvez utiliser les options suivantes pour vous authentifier auprès d’un serveur :

- Oauth
- Basic
- Ntlm

Pour utiliser l’authentification de base, il est nécessaire d’activer **Informations d’identification d’authentification alternatives** dans Azure DevOps Services, en suivant les étapes ci-dessous :

1. Connectez-vous à votre organisation Azure DevOps en tant que propriétaire (https://dev.azure.com/{organization}/{project}).

2. Dans la barre d’outils de votre organisation, sélectionnez l’icône d’engrenage et sélectionnez **Stratégie** :

    ![Option de paramètres de stratégie sélectionnée](media/tfvc-auth2.png)

3. Passez en revue les paramètres de connexion de votre application. Changez ces paramètres en fonction de vos stratégies de sécurité :

    ![Option de paramètres de stratégie sélectionnée](media/tfvc-auth.png)

### <a name="i-do-not-see-anything-in-tfvc"></a>Je ne vois rien dans TFVC

Pour définir Team Foundation Version Control (TFVC) sur votre ordinateur de développement, vous **devez** créer un espace de travail, comme décrit dans la section [Gestion des espaces de travail](#managing-workspaces).

Dans l’Explorateur du contrôle de code source, appuyez sur le bouton **Gérer les espaces de travail**. Suivez les étapes pour mapper le projet à un dossier de votre ordinateur de développement.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Je ne vois aucun de mes projets ou je ne les vois pas tous

Une fois l’authentification terminée, vous devriez voir la liste des projets. Par défaut, seuls les projets TFS sont affichés. Pour voir d’autres types de projets, cochez la case « Afficher tous les projets ».

N’oubliez pas que les projets qui se trouvent sur le serveur ne sont pas affichés si vous n’avez pas les privilèges appropriés.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>J’obtiens l’erreur « Impossible de créer l’espace de travail ». Veuillez réessayer. »

Quand vous tentez de [créer un espace de travail](#creating-a-new-workspace), vous devez vous assurer que les conditions suivantes sont remplies :

- Aucun caractère non valide dans le nom de l’espace de travail.
- Le nom doit comprendre moins de 64 caractères.
- Le chemin local ne peut pas être utilisé par d’autres espaces de travail.
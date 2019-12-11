---
title: Team Foundation Version Control (TFVC)
description: Connexion de Visual Studio pour Mac à Team Foundation Server/Azure DevOps avec Team Foundation Version Control (TFVC).
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: b7b160d58cead031a0eece2a522501d8c2060bd2
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985197"
---
# <a name="connecting-to-team-foundation-version-control"></a>Connexion à Team Foundation Version Control

> [!NOTE]
> Pour bénéficier de la meilleure expérience de gestion de version sur macOS, nous recommandons d’utiliser Git au lieu de Team Foundation Version Control (TFVC). Git est pris en charge dans Visual Studio pour Mac ; il s’agit de l’option par défaut pour les référentiels hébergés dans Team Foundation Server (TFS)/Azure DevOps. Pour en savoir plus sur Git avec TFS/Azure DevOps, voir l’article [Configurer un référentiel Git](/visualstudio/mac/set-up-git-repository).
>
> Si vous avez précédemment utilisé la version de préversion de l’extension TFVC pour Visual Studio pour Mac, elle n’est plus prise en charge lors de la mise à niveau vers Visual Studio 2019 pour Mac.

Azure Repos fournit deux modèles de contrôle de version : [git](/azure/devops/repos/git/?view=azure-devops), système de gestion de version distribué et [Team Foundation version Control](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), un système de gestion de version centralisé.

Visual Studio pour Mac assure une prise en charge complète des référentiels Git, mais des solutions de contournement sont nécessaires pour pouvoir travailler avec TFVC. Si vous utilisez actuellement TFVC pour la gestion de versions, voici quelques solutions qui vous permettront d’accéder à votre code source hébergé dans TFVC :

* [Utiliser Visual Studio Code et l’extension Azure Repos, pour une interface graphique utilisateur](#use-visual-studio-code-and-the-azure-repos-extension)
* [Se connecter au référentiel avec le client en ligne de commande Team Explorer Everywhere (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Se connecter à TFVC (Team Foundation Version Control) avec l’extension Team Foundation Version Control (non prise en charge) pour Visual Studio pour Mac](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

La suite de cet article décrit les options ci-dessus.

## <a name="requirements"></a>Configuration requise pour

* Visual Studio Community, Professional ou Enterprise pour Mac version 7.8 et ultérieure.
* Azure DevOps Services, Team Foundation Server 2013 (ou version ultérieure) ou Azure DevOps Server 2018 (ou version ultérieure).
* Un projet dans Azure DevOps Services ou Team Foundation Server/Azure DevOps Server, configuré pour utiliser Team Foundation Version Control.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Utiliser Visual Studio Code et l’extension Azure Repos

Si vous préférez travailler avec une interface graphique pour gérer vos fichiers dans la gestion de version, l’extension Azure Repos pour Visual Studio Code représente une solution Microsoft prise en charge. Pour commencer, téléchargez [Visual Studio Code](https://code.visualstudio.com) et apprenez à [configurer l’extension Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Se connecter avec le client en ligne de commande Team Explorer Everywhere

Si vous êtes à l’aise avec le terminal macOS, le client en ligne de commande Team Explorer Everywhere (TEE-CLC) représente un moyen pris en charge de vous connecter à votre source dans TFVC.

Vous pouvez suivre les étapes ci-dessous pour configurer votre connexion à TFVC et valider les modifications.

### <a name="setting-up-the-tee-clc"></a>Installer TEE-CLC

Il existe deux moyens d’installer le client TEE-CLC.

* utiliser Homebrew ;
* passer par un téléchargement et une installation manuelle.

Le plus simple est **d’utiliser HomeBrew**, un gestionnaire de package pour macOS. Pour cela :

1. Lancez l’application Terminal macOS.
1. Installez Homebrew avec le terminal suivant les instructions de la [page d’accueil de Homebrew](https://brew.sh/).
1. Une fois Homebrew installé, exécutez la commande suivante dans votre terminal : `brew install tee-clc`

Pour **configurer manuellement TEE-CLC** :

1. [Téléchargez la dernière version de TEE-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) sur la page des versions du référentiel GitHub Team Explorer Everywhere (par exemple, tee-clc-14.134.0.zip au moment de la rédaction).
1. Extrayez le contenu du fichier .zip dans un dossier sur le disque.
1. Ouvrez l’application Terminal macOS et utilisez la commande `cd` pour basculer vers le dossier utilisé à l’étape précédente.
1. Dans le dossier, exécutez la commande `./tf` pour vérifier que le client en ligne de commande peut s’exécuter ; il peut vous être demandé d’installer Java ou d’autres dépendances.

Une fois TEE-CLC installé, vous pouvez exécuter la commande `tf eula` pour afficher et accepter le contrat de licence du client.

Enfin, pour vous authentifier avec votre environnement TFS/Azure DevOps, vous devrez créer un jeton d’accès personnel sur le serveur ([en savoir plus sur l’authentification avec des jetons d’accès personnels](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops)). Lorsque vous créez et configurez un jeton d’accès personnel qui sera utilisé avec TFVC, veillez à accorder un accès complet.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Utiliser TEE-CLC pour se connecter au référentiel

Pour pouvoir vous connecter à votre code source, vous devez d’abord créer un espace de travail avec la commande `tf workspace`. Par exemple, les commandes suivantes établissent une connexion avec une organisation nommée « MyOrganization » dans Azure DevOps Services : 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Le paramètre d’environnement `TF_AUTO_SAVE_CREDENTIALS` sert à enregistrer les informations d’identification, ce qui évite d’avoir à les entrer plusieurs fois. Lorsqu’il vous est demandé un nom d’utilisateur, utilisez le jeton d’accès personnel créé dans la section précédente et un mot de passe vide.

Pour créer un mappage de vos fichiers sources à un dossier local, vous allez utiliser la commande `tf workfold`. L’exemple suivant mappe un dossier nommé « WebApp.Services » à partir du projet TFVC « MyRepository » et le configure de sorte qu’il soit copié dans le dossier local ~/Projects/ (c’est-à-dire un dossier « Projets » dans le dossier de base des utilisateurs actuels).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Enfin, utilisez la commande suivante pour obtenir les fichiers sources auprès du serveur et les copier en local :

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Valider les modifications avec TEE-CLC

Après avoir apporté des modifications à vos fichiers dans Visual Studio pour Mac, vous pouvez revenir au terminal pour archiver vos modifications. La commande `tf add` sert à ajouter des fichiers à la liste des modifications en attente d’archivage et la commande `tf checkin` effectue l’archivage proprement dit sur le serveur. La commande `checkin` comporte des paramètres permettant d’ajouter un commentaire ou d’associer un élément de travail lié. Dans l’extrait de code suivant, tous les fichiers du dossier `WebApp.Services` sont ajoutés de manière récursive à l’archivage. Ensuite, le code est archivé avec un commentaire et associé à un élément de travail portant l’ID « 42 ».

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Pour en savoir plus sur les commandes mentionnées ici, ou d’autres commandes, vous pouvez utiliser la commande suivante dans le Terminal :

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Se connecter à TFVC avec l’extension Team Foundation Version Control

> [!NOTE]
> Pour bénéficier de la meilleure expérience de gestion de version sur macOS, nous recommandons d’utiliser Git au lieu de Team Foundation Version Control (TFVC). Git est pris en charge dans Visual Studio pour Mac ; il s’agit de l’option par défaut pour les référentiels hébergés dans Team Foundation Server (TFS)/Azure DevOps. Pour en savoir plus sur Git avec TFS/Azure DevOps, voir l’article [Configurer un référentiel Git](/visualstudio/mac/set-up-git-repository).
>
> Si vous avez précédemment utilisé la version de préversion de l’extension TFVC pour Visual Studio pour Mac, elle n’est plus prise en charge lors de la mise à niveau vers Visual Studio 2019 pour Mac.

Dans la galerie d’extensions Visual Studio pour Mac, l’extension Team Foundation Version control assure une prise en charge limitée de la connexion à TFVC. Sachant qu’elle n’est pas prise en charge et comporte plusieurs problèmes connus, l’expérience qu’elle offre est variable.

Pour installer l’extension, lancez Visual Studio pour Mac, puis choisissez le menu **Visual Studio > Extensions**. Sous l’onglet **Galerie**, sélectionnez **Gestion de version > Team Foundation Version Control pour TFS et Azure DevOps** et cliquez sur **Installer…**  :

![Gestionnaire d’extensions](media/tfvc-install.png)

Suivez les invites pour installer l’extension. Une fois qu’elle est installée, redémarrez l’IDE.

### <a name="updating-the-extension"></a>Mise à jour de l’extension

Les mises à jour de l’extension TFVC sont effectuées régulièrement. Pour accéder aux mises à jour, sélectionnez **Visual Studio > extensions...** dans le menu, puis sélectionnez l’onglet **mises à jour** . Sélectionnez l’extension dans la liste et appuyez sur le bouton **mettre à jour** :

Appuyez sur **Installer** dans la boîte de dialogue suivante pour désinstaller l’ancien package et installer le nouveau.

### <a name="using-the-extension"></a>Utiliser l’extension

Une fois l’extension installée, sélectionnez l’élément de menu **Gestion de version > TFS/Azure DevOps > Ouvrir à partir du référentiel distant…** .

![Élément de menu pour ouvrir l’extension](media/tfvc-source-control-explorer-devops.png)

Choisissez VSTS ou Team Foundation Server pour démarrer, puis appuyez sur **Continuer** :

![Se connecter avec un serveur](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Authentification d’Azure Repos

Quand vous sélectionnez un projet qui est hébergé dans Azure Repos, vous êtes invité à entrer les informations de votre compte Microsoft :

![Se connecter avec Azure Repos](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>Authentification TFS

Pour vous connecter à TFS, entrez les détails du serveur et les informations d’identification de votre compte. Entrez un domaine pour utiliser l’authentification NTLM, sinon laissez vide pour utiliser l’authentification de base. Sélectionnez **Ajouter un serveur** :

![Se connecter à un serveur TFS](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Sélection d’un projet

Une fois authentifié, vous pouvez voir une liste des dépôts qui sont associés à un compte dans la boîte de dialogue **Ouvrir depuis le contrôle de code source** :

![Boîte de dialogue Ouvrir depuis le contrôle de code source avec affichage des projets](media/tfvc-vsts-projects.png)

Cette boîte de dialogue est organisée avec les nœuds suivants :

- Organisation ou collection Azure DevOps : cette option affiche toutes les organisations connectées au compte Microsoft avec lequel vous avez ouvert une session.
- Projets : dans chaque organisation ou collection, vous pouvez avoir plusieurs projets. Un projet est l’endroit où sont hébergés le code source, les éléments de travail et les builds automatisées.

À ce stade, vous pouvez effectuer une recherche et filtrer par nom de projet ou par organisation.

#### <a name="adding-a-new-server"></a>Ajout d’un nouveau serveur

Pour ajouter un nouveau serveur à la liste, appuyez sur le bouton **Ajouter un hôte** dans la boîte de dialogue **Ouvrir depuis le contrôle de code source** :

![Mise en valeur du bouton d’ajout permettant d’ajouter un nouveau serveur à la liste](media/tfvc-add-new-server.png)

Sélectionnez le fournisseur dans la liste, puis entrez vos informations d’identification :

![Boîte de dialogue affichant l’option du fournisseur de contrôle de code source](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Créer un espace de travail

Pour commencer à utiliser un projet, vous devez disposer d’un _espace de travail_. Si vous ne disposez pas d’un espace de travail, vous pouvez en créer un à partir de la zone de liste déroulante **Espace de travail** dans la boîte de dialogue **Ouvrir depuis le contrôle de code source** :

![Option de zone de liste déroulante permettant de créer un espace de travail](media/tfvc-create-new-workspace.png)

Définissez le nom et le chemin local de votre nouvel espace de travail et sélectionnez **Créer l’espace de travail** :

![Saisie du nom et du chemin local du nouvel espace de travail](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Utilisation de l’Explorateur du contrôle de code source

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

### <a name="managing-workspaces"></a>Gestion des espaces de travail

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

## <a name="troubleshooting-and-known-issues"></a>Problèmes connus et dépannage

#### <a name="problems-using-basic-authentication"></a>Problèmes avec l’authentification de base

Vous pouvez utiliser les options suivantes pour vous authentifier auprès d’un serveur :

- Oauth
- Basic
- Ntlm

Pour utiliser l’authentification de base, il est nécessaire d’activer **Informations d’identification d’authentification alternatives** dans Azure DevOps Services, en suivant les étapes ci-dessous :

1. Connectez-vous à votre organisation Azure DevOps en tant que propriétaire (https :\//dev.azure.com/{organization}/{project}).

2. Dans la barre d’outils de votre organisation, sélectionnez l’icône d’engrenage et sélectionnez **Stratégie** :

    ![Option de paramètres de stratégie sélectionnée](media/tfvc-auth2.png)

3. Passez en revue les paramètres de connexion de votre application. Changez ces paramètres en fonction de vos stratégies de sécurité :

    ![Option de paramètres de stratégie sélectionnée](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>Je ne vois rien dans TFVC

Pour définir Team Foundation Version Control (TFVC) sur votre ordinateur de développement, vous **devez** créer un espace de travail, comme décrit dans la section [Gestion des espaces de travail](#managing-workspaces).

Dans l’Explorateur du contrôle de code source, appuyez sur le bouton **Gérer les espaces de travail**. Suivez les étapes pour mapper le projet à un dossier de votre ordinateur de développement.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Je ne vois aucun de mes projets ou je ne les vois pas tous

Une fois l’authentification terminée, vous devriez voir la liste des projets. Par défaut, seuls les projets TFS sont affichés. Pour voir d’autres types de projets, cochez la case « Afficher tous les projets ».

N’oubliez pas que les projets qui se trouvent sur le serveur ne sont pas affichés si vous n’avez pas les privilèges appropriés.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>J’obtiens l’erreur « Impossible de créer l’espace de travail ». Veuillez réessayer. »

Quand vous tentez de [créer un espace de travail](#creating-a-new-workspace), vous devez vous assurer que les conditions suivantes sont remplies :

- Aucun caractère non valide dans le nom de l’espace de travail.
- Le nom doit comprendre moins de 64 caractères.
- Le chemin local ne peut pas être utilisé par d’autres espaces de travail.

### <a name="see-also"></a>Voir aussi

- [Développer et partager du code dans TFVC à l’aide de Visual Studio (sur Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)
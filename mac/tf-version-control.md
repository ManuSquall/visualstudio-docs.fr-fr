---
title: Team Foundation Version Control (TFVC)
description: Connexion de Visual Studio pour Mac à Team Foundation Server/Azure DevOps avec Team Foundation Version Control (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 06/25/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 04a251621af1086c15bafa15b7a9fe01f8dab5a8
ms.sourcegitcommit: 9d3529e40438ca45dcb0b31742c4cd5a89daa61e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398982"
---
# <a name="connecting-to-team-foundation-version-control"></a>Connexion à Team Foundation Version Control

> [!NOTE]
> Pour bénéficier de la meilleure expérience de gestion de version sur macOS, nous recommandons d’utiliser Git au lieu de Team Foundation Version Control (TFVC). Git est pris en charge dans Visual Studio pour Mac ; il s’agit de l’option par défaut pour les référentiels hébergés dans Team Foundation Server (TFS)/Azure DevOps. Pour en savoir plus sur Git avec TFS/Azure DevOps, voir l’article [Configurer un référentiel Git](/visualstudio/mac/set-up-git-repository).
> 
> Si vous avez précédemment utilisé la version de préversion de l’extension TFVC pour Visual Studio pour Mac, elle n’est plus prise en charge dans Visual Studio 2019 pour Mac.

Azure Repos propose deux modèles de gestion de versions : [Git](/azure/devops/repos/git/?view=azure-devops),un système de gestion de version distribué, et [Team Foundation Version Control](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), un système de gestion de version centralisé.

Visual Studio pour Mac assure une prise en charge complète des référentiels Git, mais des solutions de contournement sont nécessaires pour pouvoir travailler avec TFVC. Si vous utilisez actuellement TFVC pour la gestion de versions, voici quelques solutions qui vous permettront d’accéder à votre code source hébergé dans TFVC :

* [Utiliser Visual Studio Code et l’extension Azure Repos, pour une interface graphique utilisateur](#use-visual-studio-code-and-the-azure-repos-extension)
* [Se connecter au référentiel avec le client en ligne de commande Team Explorer Everywhere (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

La suite de cet article décrit les options ci-dessus.

## <a name="requirements"></a>Configuration requise

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

Enfin, pour vous authentifier avec votre environnement TFS/Azure DevOps, vous devrez créer un jeton d’accès personnel sur le serveur ([en savoir plus sur l’authentification avec des jetons d’accès personnels](https://docs.microsoft.com/azure/devops/integrate/get-started/authentication/pats?view=azure-devops)). Lorsque vous créez et configurez un jeton d’accès personnel qui sera utilisé avec TFVC, veillez à accorder un accès complet.

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

### <a name="see-also"></a>Voir aussi

- [Développer et partager du code dans TFVC à l’aide de Visual Studio (sur Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)
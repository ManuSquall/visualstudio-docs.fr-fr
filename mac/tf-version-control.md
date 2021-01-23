---
title: Team Foundation Version Control (TFVC)
description: Guide de dépannage sur TFVC et macOS.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: 11b0788317cd0a20dd27159aa241db32e3818daf
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722124"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Visual Studio pour Mac prend-il en charge Team Foundation Version Control ?

> [!CAUTION]
> La préversion de l’extension TFVC pour Visual Studio pour Mac n’est plus prise en charge dans Visual Studio 2019 pour Mac.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Options Version Control alternatives dans Visual Studio pour Mac

Pour une expérience de contrôle de version optimale sur macOS, nous vous recommandons d’utiliser **git** au lieu de Team Foundation version Control (TFVC). 

Git est pris en charge dans Visual Studio pour Mac ; il s’agit de l’option par défaut pour les référentiels hébergés dans Team Foundation Server (TFS)/Azure DevOps. Pour en savoir plus sur Git avec TFS/Azure DevOps, consultez le guide [Configurer un référentiel Git](./set-up-git-repository.md).

## <a name="unsupported-workarounds-for-tfvc"></a>Solutions de contournement non prises en charge pour TFVC

Bien que Visual Studio pour Mac ne prenne pas en charge TFVC officiellement, le reste de ce guide fournit des solutions de contournement pour travailler avec TFVC sur macOS. Si vous utilisez actuellement TFVC pour la gestion de versions, voici quelques solutions qui vous permettront d’accéder à votre code source hébergé dans TFVC :

* Option 1. [ Utiliser Visual Studio Code et l’extension Azure Repos pour une interface utilisateur graphique](#use-visual-studio-code-and-the-azure-repos-extension)
* Option 2. [Se connecter au référentiel avec le client en ligne de commande Team Explorer Everywhere (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>Option 1. <a id="use-visual-studio-code-and-the-azure-repos-extension"></a> Utiliser Visual Studio Code et l’extension Azure Repos

Si vous préférez travailler avec une interface graphique pour gérer vos fichiers dans la gestion de version, l’extension Azure Repos pour Visual Studio Code représente une solution Microsoft prise en charge. Pour commencer, téléchargez [Visual Studio Code](https://code.visualstudio.com) et apprenez à [configurer l’extension Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>Option 2. <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a> Connexion à l’aide du client de ligne de commande Team Explorer Everywhere

> [!IMPORTANT]
> Comme pour le fichier Lisez-moi Team Explorer Everywhere, ce projet [n’est plus conservé](https://github.com/microsoft/team-explorer-everywhere).

Si vous êtes à l’aise avec le terminal macOS, le client en ligne de commande Team Explorer Everywhere (TEE-CLC) représente un moyen pris en charge de vous connecter à votre source dans TFVC.

Vous pouvez suivre les étapes ci-dessous pour configurer votre connexion à TFVC et valider les modifications.

#### <a name="setting-up-the-tee-clc"></a>Installer TEE-CLC

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

Enfin, pour vous authentifier avec votre environnement TFS/Azure DevOps, vous devrez créer un jeton d’accès personnel sur le serveur ([en savoir plus sur l’authentification avec des jetons d’accès personnels](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops&preserve-view=true)). Lorsque vous créez et configurez un jeton d’accès personnel qui sera utilisé avec TFVC, veillez à accorder un accès complet.

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Utiliser TEE-CLC pour se connecter au référentiel

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

#### <a name="committing-changes-using-the-tee-clc"></a>Valider les modifications avec TEE-CLC

Après avoir apporté des modifications à vos fichiers dans Visual Studio pour Mac, vous pouvez revenir au terminal pour archiver vos modifications. La commande `tf add` sert à ajouter des fichiers à la liste des modifications en attente d’archivage et la commande `tf checkin` effectue l’archivage proprement dit sur le serveur. La commande `checkin` comporte des paramètres permettant d’ajouter un commentaire ou d’associer un élément de travail lié. Dans l’extrait de code suivant, tous les fichiers du dossier `WebApp.Services` sont ajoutés de manière récursive à l’archivage. Ensuite, le code est archivé avec un commentaire et associé à un élément de travail portant l’ID « 42 ».

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Pour en savoir plus sur les commandes mentionnées ici, ou d’autres commandes, vous pouvez utiliser la commande suivante dans le Terminal :

`tf help`

## <a name="see-also"></a>Voir aussi

- [Développer et partager votre code dans TFVC avec Visual Studio (sur Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)
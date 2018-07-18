---
title: Déploiement de Pages de démarrage personnalisées | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2cdbd301d48b0133268a40614178040271fcfc34
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237638"
---
# <a name="deploy-custom-start-pages"></a>Déployer les Pages de démarrage personnalisées

Vous pouvez déployer les Pages de démarrage personnalisées à l’aide de déploiement VSIX ou en copiant les fichiers aux emplacements appropriés sur l’ordinateur cible.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Déploiement VSIX à l’aide du modèle de projet de Page de démarrage

Lorsque vous créez une Page de démarrage en utilisant le modèle de projet Page de démarrage, puis générez le projet, Visual Studio crée un fichier .vsix que vous pouvez distribuer. Empaquetage d’une Page de démarrage dans un fichier .vsix vous offre les options suivantes pour le déploiement, en fonction de votre public ciblé :

-   Vous pouvez placer le fichier .vsix sur un partage réseau ou sur un site Web public. Quand un utilisateur ouvre le fichier, la Page de démarrage est automatiquement installée.

-   Vous pouvez télécharger le fichier .vsix sur le [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) afin que les utilisateurs peuvent l’installer à l’aide de site Web **Gestionnaire d’extensions**.

Le modèle de projet Page de démarrage crée une copie de la Page de démarrage de Visual Studio par défaut afin que vous puissiez modifier la copie et conserver l’original.

Vous pouvez obtenir le modèle de projet Page de démarrage à l’aide de **Gestionnaire d’extensions** ou en le téléchargeant à partir du site Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Déploiement VSIX sans utiliser le modèle de projet de Page de démarrage
 Réussite du déploiement VSIX requiert une extension pour être installés dans des dossiers qui sont reconnus par le processus d’inscription VSIX et par **Gestionnaire d’extensions**. Étant donné que le modèle de projet Page de démarrage spécifie déjà les dossiers appropriés, nous recommandons d’utiliser chaque fois que vous souhaitez un package d’extension pour le déploiement VSIX. Toutefois, si vous avez un cas dans lequel vous ne pouvez pas utiliser le modèle, vous pouvez créer un déploiement VSIX sans l’utiliser.

 Pour créer un déploiement VSIX sans utiliser le modèle de projet Page de démarrage, commencez par créer un fichier .vsix pour la Page de démarrage dans une des deux façons suivantes :

-   En ajoutant vos fichiers de Page de démarrage personnalisées à un projet VSIX vide. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).

-   En créant manuellement un fichier .vsix. Pour créer manuellement un fichier .vsix :

    1.  Créer le fichier extension.vsixmanifest et le fichier [Content_Types] .xml dans un nouveau dossier. Pour plus d’informations, consultez [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md).

    2.  Dans l’Explorateur Windows, cliquez sur le dossier qui contient les deux fichiers XML, cliquez sur Envoyer vers, puis cliquez sur dossier compressé (zippé). Renommez le fichier .zip à Filename.vsix, où nom_fichier représente le nom du fichier redistribuable qui installe votre package.

 Pour Visual Studio de reconnaître une Page de démarrage, le `Content Element` du manifeste VSIX doit contenir un `CustomExtension Element` qui a le `Type` attribut la valeur `"StartPage"`. Une extension de la Page de démarrage qui a été installée à l’aide de déploiement VSIX s’affiche dans le **personnaliser la Page de démarrage** liste sur le **démarrage** page d’options en tant que **[Extension installée]** *Nom de l’extension*.

 Si votre package de la Page de démarrage inclut des assemblys, vous devez ajouter l’inscription de chemin d’accès de liaison afin qu’ils soient disponibles au démarrage de Visual Studio. Pour ce faire, assurez-vous que votre package inclut un fichier .pkgdef qui comporte les informations suivantes.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Déploiement VSIX pour tous les utilisateurs
 Par défaut, les extensions déployées dans les packages VSIX installent uniquement pour l’utilisateur actuel. Faire une installation de la Page de démarrage pour tous les utilisateurs de la machine cible en créant un déploiement pour tous les utilisateurs.

#### <a name="to-create-an-all-users-deployment"></a>Pour créer un déploiement pour tous les utilisateurs

1.  Ouvrez le fichier extension.vsixmanifest en mode code.

2.  Dans le `Identifier` élément du manifeste vsix, ajoutez un `AllUsers` élément qui a la valeur `true`.

    ```
    <AllUsers>true</AllUsers>
    ```

     Ainsi, le programme d’installation de vsix demander des autorisations d’administrateur et ensuite installer les fichiers sur \Common7\IDE\Extensions.

3.  Ouvrez le fichier .pkgdef.

4.  Modifier le .pkgdef pour définir la page de démarrage par défaut sous HKLM en ajoutant le code suivant, où *MyStartPage.xaml* est le nom du fichier .xaml qui contient votre Page de démarrage.

     [$RootKey$ \StartPage\Default]

     « Uri « = » $PackageFolder$\\*MyStartPage.xaml*»

     Ce code indique à Visual debout à rechercher dans le nouvel emplacement de la Page de démarrage.

## <a name="file-copy-deployment"></a>Déploiement de copie de fichier
 Il est inutile de créer un fichier .vsix pour déployer une Page de démarrage personnalisée. Au lieu de cela, vous pouvez copier le balisage et les fichiers de prise en charge directement dans le dossier \StartPages\ de l’utilisateur. Le **personnaliser la Page de démarrage** liste sur le **démarrage** page options répertorie chaque fichier .xaml dans ce dossier, ainsi que le chemin d’accès, par exemple, %USERPROFILE%\My Documents\Visual Studio  *version*\StartPages\\*nom de fichier*.xaml. Si votre Page de démarrage inclut des références aux assemblys privés, vous devez copiez-les et collez-les dans le dossier \PrivateAssemblies\.

 Pour distribuer une Page de démarrage que vous avez créé sans empaquetage dans un fichier .vsix, nous recommandons que vous utilisez une stratégie de copie de fichier de base, par exemple, un script de commandes, ou toute autre technologie de déploiement qui vous permet de placer les fichiers dans les répertoires requis.

### <a name="to-manually-install-a-custom-start-page"></a>Pour installer manuellement une Page de démarrage personnalisée

1.  Copiez le fichier .xaml qui contient le balisage de Page de démarrage, ainsi que les fichiers autres que des assemblys et les coller dans le dossier \StartPages\ de l’utilisateur.

2.  Si la Page de démarrage requiert des assemblys, copiez-les et collez-les dans... \\ *Dossier d’installation de visual Studio*\Common7\IDE\PrivateAssemblies\\.

3.  Dans le **personnaliser la Page de démarrage** liste sur le **démarrage** options, sélectionnez la nouvelle Page de démarrage. Pour plus d’informations, consultez [Personnalisation de la page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Personnalisation de la page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md)
- [Ajout d’un contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)
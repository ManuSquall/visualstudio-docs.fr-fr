---
title: Déploiement des pages de démarrage personnalisées | Microsoft Docs
description: Découvrez comment déployer des pages de démarrage personnalisées à l’aide d’un déploiement VSIX ou en copiant les fichiers aux emplacements corrects sur l’ordinateur cible.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3deac1637bb6b4ed054a8a9afc7ab78bf26d0183
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968409"
---
# <a name="deploy-custom-start-pages"></a>Déployer des pages de démarrage personnalisées

Vous pouvez déployer des pages de démarrage personnalisées à l’aide du déploiement VSIX ou en copiant les fichiers aux emplacements appropriés sur l’ordinateur cible.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Déploiement VSIX à l’aide du modèle de projet page de démarrage

Quand vous créez une page de démarrage à l’aide du modèle de projet page de démarrage, puis que vous générez le projet, Visual Studio crée un fichier *. vsix* que vous pouvez distribuer. L’empaquetage d’une page de démarrage dans un fichier *. vsix* vous offre les options de déploiement suivantes, en fonction de votre public ciblé :

- Vous pouvez placer le fichier *. vsix* sur un partage réseau ou sur un site Web public. Quand un utilisateur ouvre le fichier, la page de démarrage est automatiquement installée.

- Vous pouvez télécharger le fichier *. vsix* sur le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) afin que les utilisateurs puissent l’installer à l’aide du **Gestionnaire d’extensions**.

Le modèle de projet page de démarrage crée une copie de la page de démarrage de Visual Studio par défaut, ce qui vous permet de modifier la copie et de conserver l’original.

Vous pouvez obtenir le modèle de projet page de démarrage à l’aide du **Gestionnaire d’extensions** ou en le téléchargeant à partir du site Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Déploiement VSIX sans utiliser le modèle de projet page de démarrage
 Pour réussir un déploiement VSIX, vous devez installer une extension dans des dossiers reconnus par le processus d’inscription VSIX et par le **Gestionnaire d’extensions**. Étant donné que le modèle de projet page de démarrage spécifie déjà les dossiers corrects, nous vous recommandons de l’utiliser chaque fois que vous souhaitez empaqueter une extension pour le déploiement VSIX. Toutefois, si vous ne pouvez pas utiliser le modèle, vous pouvez créer un déploiement VSIX sans l’utiliser.

 Pour créer un déploiement VSIX sans utiliser le modèle de projet page de démarrage, commencez par créer un fichier *. vsix* pour la page de démarrage de l’une des deux manières suivantes :

- En ajoutant vos fichiers de page de démarrage personnalisés à un projet VSIX vide. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).

- En créant manuellement un fichier *. vsix* . Pour créer un fichier *. vsix* manuellement :

   1. Créez le fichier *extension. vsixmanifest* et le fichier *[Content_Types]. xml* dans un nouveau dossier. Pour plus d’informations, consultez [anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. Dans l’Explorateur Windows, cliquez avec le bouton droit sur le dossier qui contient les deux fichiers XML, cliquez sur **Envoyer vers**, puis sur dossier compressé (zippé). Renommez le fichier *. zip* résultant en *nom_fichier. vsix*, où nom_fichier est le nom du fichier redistribuable qui installe votre package.

Pour que Visual Studio reconnaisse une page de démarrage, le `Content Element` du manifeste VSIX doit contenir un `CustomExtension Element` dont l’attribut a la `Type` valeur `"StartPage"` . Une extension de page de démarrage qui a été installée à l’aide du déploiement VSIX apparaît dans la liste **personnaliser la page** de démarrage de la page Options de **démarrage** en tant que *nom d’extension* **[extension installée]** .

Si votre package de page de démarrage comprend des assemblys, vous devez ajouter l’inscription du chemin de liaison afin qu’ils soient disponibles au démarrage de Visual Studio. Pour ce faire, assurez-vous que votre package inclut un fichier *. pkgdef* contenant les informations suivantes.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Déploiement VSIX pour tous les utilisateurs
 Par défaut, les extensions déployées dans les packages VSIX s’installent uniquement pour l’utilisateur actuel. Vous pouvez effectuer l’installation d’une page de démarrage pour tous les utilisateurs de l’ordinateur cible en créant un déploiement de All-Users.

### <a name="to-create-an-all-users-deployment"></a>Pour créer un déploiement de All-Users

1. Ouvrez le fichier *extension. vsixmanifest* en mode Code.

2. Dans l' `Identifier` élément du manifeste VSIX, ajoutez un `AllUsers` élément qui a la valeur `true` .

    ```
    <AllUsers>true</AllUsers>
    ```

     Cela amène le programme d’installation VSIX à demander des autorisations d’administrateur, puis à installer les fichiers sur *\Common7\IDE\Extensions*.

3. Ouvrez le fichier *. pkgdef* .

4. Modifiez le fichier *. pkgdef* pour définir la page de démarrage par défaut sous HKLM en ajoutant le code suivant, où *MyStartPage. Xaml* est le nom du fichier *. Xaml* qui contient votre page de démarrage.

     [$RootKey $ \StartPage\Default]

     "URI" = "$PackageFolder $ \\ *MyStartPage. Xaml*"

     Cela indique à Visual Studio de rechercher le nouvel emplacement de la page de démarrage.

## <a name="file-copy-deployment"></a>Déploiement de copie de fichiers
 Vous n’avez pas besoin de créer un fichier *. vsix* pour déployer une page de démarrage personnalisée. Au lieu de cela, vous pouvez copier le balisage et les fichiers de prise en charge directement dans le dossier \StartPages de l’utilisateur <em> \* . La liste **personnaliser la page de démarrage</em>* de la page Options de **démarrage** répertorie chaque fichier *. Xaml* de ce dossier, ainsi que le chemin d’accès, par exemple, *%UserProfile%\My Documents\Visual Studio {version} \StartPages \\ {nom de fichier}. Xaml*. Si votre page de démarrage contient des références à des assemblys privés, vous devez les copier et les coller dans le dossier * \PrivateAssemblies \* .

 Pour distribuer une page de démarrage que vous avez créée sans l’empaqueter dans un fichier *. vsix* , nous vous recommandons d’utiliser une stratégie de copie de base de fichiers, par exemple un script de commandes ou toute autre technologie de déploiement qui vous permet de placer les fichiers dans les répertoires requis.

### <a name="to-manually-install-a-custom-start-page"></a>Pour installer manuellement une page de démarrage personnalisée

1. Copiez le fichier *. Xaml* qui contient le balisage de la page de démarrage, ainsi que tous les fichiers de prise en charge autres que les assemblys, puis collez-les dans le dossier * \StartPages de l’utilisateur \* .

2. Si la page de démarrage requiert des assemblys, copiez-les et collez-les dans *. \\ {Dossier d’installation de Visual Studio \\ } \Common7\IDE\PrivateAssemblies*.

3. Dans la liste **personnaliser la page** de démarrage de la page Options de **démarrage** , sélectionnez la nouvelle page de démarrage. Pour plus d’informations, consultez [personnaliser la page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Personnaliser la page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md)
- [Ajouter un contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)

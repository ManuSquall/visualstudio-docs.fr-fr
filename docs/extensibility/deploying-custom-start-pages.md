---
title: Déploiement de pages de démarrage personnalisées (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 210b4589c0e2165af537c3fa9129affb06197e9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712228"
---
# <a name="deploy-custom-start-pages"></a>Déployer des pages de démarrage personnalisées

Vous pouvez déployer des pages de démarrage personnalisées en utilisant le déploiement VSIX ou en copiant les fichiers aux emplacements corrects sur l’ordinateur cible.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Déploiement VSIX en utilisant le modèle de projet Start Page

Lorsque vous créez une page de démarrage en utilisant le modèle de projet Start Page, puis construisez le projet, Visual Studio crée un fichier *.vsix* que vous pouvez distribuer. L’emballage d’une page de démarrage dans un fichier *.vsix* vous offre les options de déploiement suivantes, selon votre audience prévue :

- Vous pouvez mettre le fichier *.vsix* sur une part de réseau ou sur un site Web public. Lorsque quelqu’un ouvre le fichier, la page de démarrage est automatiquement installée.

- Vous pouvez télécharger le fichier *.vsix* sur le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) afin que les utilisateurs puissent l’installer en utilisant Extension **Manager**.

Le modèle de projet Start Page crée une copie de la page de démarrage visual visual visual par défaut afin que vous puissiez modifier la copie et préserver l’original.

Vous pouvez obtenir le modèle de projet Start Page en utilisant **Extension Manager** ou en le téléchargeant à partir du site Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Déploiement VSIX sans utiliser le modèle de projet Start Page
 Un déploiement VSIX réussi nécessite une extension à installer dans les dossiers qui sont reconnus par le processus d’enregistrement VSIX et par **Le gestionnaire d’extension**. Étant donné que le modèle de projet Start Page spécifie déjà les dossiers corrects, nous vous recommandons de l’utiliser chaque fois que vous souhaitez emballer une extension pour le déploiement VSIX. Toutefois, si vous avez un cas dans lequel vous ne pouvez pas utiliser le modèle, vous pouvez créer un déploiement VSIX sans l’utiliser.

 Pour créer un déploiement VSIX sans utiliser le modèle de projet Start Page, créez d’abord un fichier *.vsix* pour la page de démarrage de l’une ou l’autre de ces deux façons :

- En ajoutant vos fichiers De page de démarrage personnalisés à un projet VSIX vide. Pour plus d’informations, consultez [le modèle de projet VSIX](../extensibility/vsix-project-template.md).

- En créant manuellement un fichier *.vsix.* Pour créer un fichier *.vsix* manuellement :

   1. Créez le fichier *extension.vsixmanifest* et le fichier *[Content_Types].xml* dans un nouveau dossier. Pour plus d’informations, voir [Anatomie d’un forfait VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. Dans Windows Explorer, cliquez à droite sur le dossier qui contient les deux fichiers XML, cliquez sur **Envoyer à**, puis cliquez sur Compressed (zipped) Dossier. Rebaptisez le fichier *.zip* résultant à *Filename.vsix*, où Filename est le nom du fichier redistributable qui installe votre colis.

Pour que Visual Studio reconnaisse une page de démarrage, `Content Element` le manifeste VSIX doit contenir un `CustomExtension Element` qui a l’attribut `Type` fixé à `"StartPage"`. Une extension de la page de démarrage qui a été installée en utilisant le déploiement VSIX apparaît dans la liste de la **page de démarrage personnalisée** sur la page d’options **Startup** sous le nom **d’extension [Extension installée]** *Extension Name*.

Si votre forfait Page De démarrage comprend des assemblages, vous devez ajouter l’enregistrement du chemin de liaison afin qu’ils soient disponibles lorsque Visual Studio commence. Pour ce faire, assurez-vous que votre colis comprend un fichier *.pkgdef* qui a les informations suivantes.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Déploiement VSIX pour tous les utilisateurs
 Par défaut, les extensions déployées dans les paquets VSIX ne s’installent que pour l’utilisateur actuel. Vous pouvez installer une page de démarrage pour tous les utilisateurs de la machine cible en créant un déploiement All-Users.

### <a name="to-create-an-all-users-deployment"></a>Créer un déploiement Tous utilisateurs

1. Ouvrez le fichier *extension.vsixmanifest* en vue de code.

2. Dans `Identifier` l’élément du manifeste vsix, ajouter `AllUsers` un `true`élément qui a une valeur de .

    ```
    <AllUsers>true</AllUsers>
    ```

     Cela provoque l’installateur vsix à inviter pour les autorisations de l’administrateur, puis installer les fichiers à *'Common7 'IDE 'Extensions*.

3. Ouvrez le fichier *.pkgdef.*

4. Modifier le *.pkgdef* pour définir la page de démarrage par défaut sous HKLM en ajoutant ce qui suit, où *MyStartPage.xaml* est le nom du fichier *.xaml* qui contient votre page de démarrage.

     [$RootKey$-StartPage-Default]

     "Uri" $PackageFolder$\\*MyStartPage.xaml*"

     Cela permet à Visual Studio de regarder dans le nouvel emplacement De la page de démarrage.

## <a name="file-copy-deployment"></a>Déploiement de copie de fichier
 Vous n’avez pas à créer un fichier *.vsix* pour déployer une page de démarrage personnalisée. Au lieu de cela, vous pouvez copier les fichiers de balisage et de soutien directement dans le dossier De l’utilisateur <em>'StartPages.\* La*Customize Start Page</em> * liste de la page de démarrage personnalisée sur la page d’options **Startup** répertorie chaque fichier *.xaml* dans ce dossier, ainsi que le chemin, par exemple, *%USERPROFILE% -My Documents’Visual Studio 'version''StartPages\\'File Name'.xaml*. Si votre page de démarrage comprend des références à des assemblages privés, vous\* devez les copier et les coller dans le dossier d’assemblage privé.

 Pour distribuer une page de démarrage que vous avez créée sans l’emballer dans un fichier *.vsix,* nous vous recommandons d’utiliser une stratégie de copie de fichier de base, par exemple, un script de lot, ou toute autre technologie de déploiement qui vous permet de mettre les fichiers dans les répertoires requis.

### <a name="to-manually-install-a-custom-start-page"></a>Pour installer manuellement une page de démarrage personnalisée

1. Copiez le fichier *.xaml* qui contient la balisage de la page de démarrage, ainsi que tous\* les fichiers à l’appui autres que les assemblages, et collez-les dans le dossier StartPages de l’utilisateur.

2. Si la page de démarrage nécessite des assemblages, copiez-les et collez-les en *.. Dossier d’installation de studio visuel ' Common7'IDE’PrivateAssemblies\\. \\*

3. Dans la liste de la **page De démarrage personnalisée** sur la page d’options **Startup,** sélectionnez la nouvelle page de démarrage. Pour plus d’informations, voir [Personnaliser la page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Personnaliser la page de départ](../ide/customizing-the-start-page-for-visual-studio.md)
- [Ajouter le contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)

---
title: Inclusion d’un package NuGet dans votre projet
description: Ce document explique comment inclure un package NuGet dans un projet à l’aide de Visual Studio pour Mac. Il décrit la recherche et le téléchargement d’un package, et il présente les fonctionnalités d’intégration de l’IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/04/2020
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: e361a1a0fba05a6fdabc66b03008049dfa34784f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349320"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Installer et gérer des packages NuGet dans Visual Studio pour Mac

L’interface utilisateur du gestionnaire de package NuGet dans Visual Studio pour Mac vous permet d’installer, de désinstaller et de mettre à jour facilement des packages NuGet dans des projets et des solutions. Vous pouvez rechercher et ajouter des packages à vos projets .NET Core, ASP.NET Core et Xamarin.

Cet article explique comment inclure un package NuGet dans un projet. De plus, il présente la chaîne d’outils qui permet d’exécuter le processus sans interruption.

Pour une introduction à l’utilisation de NuGet dans Visual Studio pour Mac, consultez [démarrage rapide : installer et utiliser un package dans Visual Studio pour Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Rechercher et installer un package

1. Avec un projet ouvert dans Visual Studio pour Mac, cliquez avec le bouton droit sur le dossier **dépendances** (dossier **packages** si vous utilisez un projet Xamarin) dans le **panneau solutions** puis sélectionnez **gérer les packages NuGet...**.

    ![Action contextuelle Ajouter un nouveau package NuGet](media/nuget-walkthrough-packages-menu.png)

2. La fenêtre **gérer les packages NuGet** s’ouvre. Assurez-vous que la liste déroulante source dans le coin supérieur gauche de la boîte de dialogue est définie sur `nuget.org` , afin que vous effectuiez une recherche dans le référentiel de package NuGet central.

    ![Répertorier les packages NuGet](media/nuget-walkthrough-add-packages1.png)

3. Utilisez la zone de recherche dans le coin supérieur droit pour rechercher un package spécifique, par exemple `EntityFramework`. Une fois que vous avez trouvé un package à utiliser, sélectionnez-le, puis cliquez sur le bouton **Ajouter le package** pour commencer l’installation.

    ![Ajouter un package NuGet EntityFramework](media/nuget-walkthrough-add-packages2.png)

4. Une fois le package téléchargé, il est ajouté à votre projet. La solution change en fonction du type de projet que vous modifiez :

    **Projets Xamarin**
    * Le nœud **Références** contient une liste de tous les assemblys qui font partie d’un package NuGet.
    * Le nœud **Packages** montre chaque package NuGet que vous avez téléchargé. Vous pouvez mettre à jour ou supprimer un package dans cette liste.
    
    **Projets .NET Core**

    * Le nœud **dépendances > NuGet** affiche chaque package NuGet que vous avez téléchargé. Vous pouvez mettre à jour ou supprimer un package dans cette liste.

## <a name="using-nuget-packages"></a>Utilisation de packages NuGet

Une fois le package NuGet ajouté et les références du projet mises à jour, vous pouvez programmer en utilisant les API comme vous le feriez avec n’importe quelle référence de projet.

Veillez à ajouter les directives `using` nécessaires en haut de votre fichier :

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Mise à jour des packages

Les mises à jour de package peuvent être effectuées en une seule fois, en cliquant avec le bouton droit sur le nœud **dépendances** (nœud **packages** pour les projets Xamarin) ou individuellement sur chaque package. Quand une nouvelle version d’un package NuGet est disponible, une icône de mise à jour s’affiche ![ avec un cercle ](media/nuget-walkthrough-update-icon.png) .

Cliquez avec le bouton droit sur **dépendances** pour accéder au menu contextuel, puis choisissez **mettre** à jour pour mettre à jour tous les packages :

![Menu contextuel des dépendances avec le menu mettre à jour mis en surbrillance](media/nuget-walkthrough-packages-menu-update.png)

* **Gérer les packages NuGet** : ouvre la fenêtre pour ajouter d’autres packages au projet.
* **Mettre à jour**  : recherche les versions les plus récentes des packages sur le serveur source et les télécharge.
* **Restaurer**  : télécharge les packages manquants (sans mettre à jour les packages existants vers leur version la plus récente).

Les options Mettre à jour et Restaurer sont également disponibles au niveau de la solution, et elles affectent tous les projets de la solution.

### <a name="updating-to-pre-release-versions-of-packages"></a>Mise à jour vers les versions préliminaires des packages
Pour effectuer une mise à jour vers une version préliminaire plus récente d’un package, vous pouvez cliquer avec le bouton droit sur **dépendances** pour ouvrir le menu contextuel et choisir le menu **gérer les packages NuGet...** .

![Menu contextuel des dépendances avec gérer les packages NuGet... menu en surbrillance](media/nuget-walkthrough-packages-menu-manage-nuget-packages.png)

Cochez la case **afficher les packages** de préversion en bas de la boîte de dialogue.

![Boîte de dialogue gérer les packages NuGet ouverte avec l’option « Afficher les packages en version préliminaire » activée](media/nuget-walkthrough-show-pre-release-packages.png)

Enfin, dans l’onglet **mises à jour** de la boîte de dialogue, sélectionnez le package que vous souhaitez mettre à jour, puis choisissez la nouvelle version préliminaire dans la liste déroulante **nouvelle version** , puis cliquez sur **mettre à jour le package**.

![Boîte de dialogue gérer les packages NuGet ouverte à l’onglet installé, avec un package sélectionné et la liste déroulante nouvelle version ouverte.](media/nuget-walkthrough-packages-nuget-dialog-update-installed-package.png)

### <a name="locating-outdated-packages"></a>Recherche de packages obsolètes
Dans le panneau solutions, vous pouvez afficher la version d’un package actuellement installée et cliquer avec le bouton droit sur le package à mettre à jour.

![Menu packages avec les options de mise à jour, de suppression et d’actualisation](media/nuget-walkthrough-PackageMenu.png)

Vous verrez également une notification en regard du nom du package lorsqu’une nouvelle version d’un package est disponible. vous pouvez donc décider si vous souhaitez la mettre à jour.

![Notification affichée lorsqu’une nouvelle version de package est disponible](media/nuget-walkthrough-package-update-available.png)

Dans le menu qui s’affiche, vous avez deux options :

* **Mettre à jour**  : recherche une version plus récente sur le serveur source et si elle existe, la télécharge.
* **Supprimer**  : supprime le package de ce projet et supprime les assemblys concernés des références du projet.

## <a name="manage-packages-for-the-solution"></a>Gérer des packages pour la solution

La gestion des packages pour une solution est un moyen pratique de travailler simultanément sur plusieurs projets.

1. Cliquez avec le bouton droit sur la solution et sélectionnez **gérer les packages NuGet...** :

    ![Gérer les packages NuGet pour la solution](media/nuget-walkthrough-manage-packages-solution.png)

1. Lorsque vous gérez des packages pour la solution, l’interface utilisateur vous permet de sélectionner les projets affectés par les opérations :

    ![Sélecteur de projet lors de la gestion de packages pour la solution](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Onglet Consolider

Quand vous travaillez dans une solution avec plusieurs projets, il est considéré comme une bonne pratique de s’assurer que partout où vous utilisez le même package NuGet dans chaque projet, vous utilisez également le même numéro de version de ce package. Visual Studio pour Mac facilite cela en fournissant un onglet **consolider** dans l’interface utilisateur du gestionnaire de package lorsque vous choisissez de gérer les packages d’une solution. À l’aide de cet onglet, vous pouvez facilement voir où les packages avec des numéros de version distincts sont utilisés par différents projets dans la solution :

![Onglet Consolider de l’interface utilisateur du gestionnaire de package](media/nuget-walkthrough-consolidate-tab.png)

Dans cet exemple, le projet NuGetDemo utilise Microsoft. EntityFrameworkCore 2,20, alors que NuGetDemo. Shared utilise Microsoft. EntityFrameworkCore 2.2.6. Pour consolider les versions de package, procédez comme suit :

- Sélectionnez les projets à mettre à jour dans la liste des projets.
- Sélectionnez la version à utiliser dans tous les projets de la **nouvelle liste version** , par exemple Microsoft. EntityFrameworkCore 3.0.0.
- Sélectionnez le bouton **consolider le package** .

Le gestionnaire de package installe la version de package sélectionnée dans tous les projets sélectionnés, après quoi le package ne s'affiche plus sous l’onglet **Consolider**.

## <a name="adding-package-sources"></a>Ajout de sources de packages

Les packages disponibles pour l’installation sont initialement récupérés à partir de nuget.org. Toutefois, vous pouvez ajouter d’autres emplacements de package à Visual Studio pour Mac. Ceci peut être pratique pour tester vos propres packages NuGet en cours de développement, ou pour utiliser un serveur NuGet privé au sein de votre entreprise ou organisation.

Dans Visual Studio pour Mac, accédez à **Visual Studio > préférences > les sources de > NuGet** pour afficher et modifier la liste des sources de packages. Notez que les sources peuvent être un serveur distant (spécifié par une URL) ou un répertoire local.

![Sources de packages](media/nuget-walkthrough-PackageSource.png)

Cliquez sur **Ajouter** pour configurer une nouvelle source. Entrez un nom convivial et l’URL (ou le chemin du fichier) vers la source du package. Si la source est un serveur web sécurisé, entrez le nom d’utilisateur et le mot de passe, sinon laissez ces entrées vides :

![Boîte de dialogue Ajouter une source de package avec une invite pour le nom, l’URL d’emplacement, le nom d’utilisateur et le mot de passe.](media/nuget-walkthrough-PackageSource2.png)

Vous pouvez sélectionner différentes sources lors de la recherche de packages :

![Boîte de dialogue Ajouter une source de package présentant une liste déroulante contenant une liste de sources de package.](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Gestion de version

La documentation de NuGet traite de [l’utilisation de NuGet sans validation des packages auprès de contrôle de code source](/nuget/consume-packages/packages-and-source-control). Si vous préférez ne pas stocker les fichiers binaires et les informations non utilisées dans le contrôle de code source, vous pouvez configurer Visual Studio pour Mac pour restaurer automatiquement les packages à partir du serveur. En d’autres termes, quand un développeur récupère le projet à partir du contrôle de code source pour la première fois, Visual Studio pour Mac télécharge et installe automatiquement les packages nécessaires.

![Restaurer automatiquement les packages](media/nuget-walkthrough-AutoRestore.png)

Pour plus d’informations sur la façon d’exclure le répertoire `packages` du suivi, consultez la documentation spécifique à votre contrôle de code source.

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Voir aussi

* [Installer et utiliser un package dans Visual Studio (sur Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

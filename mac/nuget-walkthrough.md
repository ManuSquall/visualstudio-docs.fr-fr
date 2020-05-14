---
title: Inclusion d’un package NuGet dans votre projet
description: Ce document couvre la façon d’inclure un paquet NuGet dans un projet utilisant Visual Studio pour Mac. Il décrit la recherche et le téléchargement d’un package, et il présente les fonctionnalités d’intégration de l’IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74127240"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Installer et gérer des forfaits NuGet dans Visual Studio pour Mac

L’interface utilisateur NuGet Package Manager dans Visual Studio pour Mac vous permet d’installer, de désinstaller et de mettre à jour facilement les paquets NuGet dans des projets et des solutions. Vous pouvez rechercher et ajouter des paquets à vos projets .NET Core, ASP.NET Core et Xamarin.

Cet article explique comment inclure un package NuGet dans un projet. De plus, il présente la chaîne d’outils qui permet d’exécuter le processus sans interruption.

Pour une intro à l’aide de NuGet dans Visual Studio pour Mac, voir [Quickstart: Installer et utiliser un paquet dans Visual Studio pour Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Trouver et installer un paquet

1. Avec un projet ouvert dans Visual Studio pour Mac, cliquez à droite sur le dossier **Dépendances** (dossier**de paquets** si vous utilisez un projet Xamarin) dans le **solution Pad** et **sélectionnez Manage NuGet Packages...**.

    ![Action contextuelle Ajouter un nouveau package NuGet](media/nuget-walkthrough-packages-menu.png)

2. Cela lance la fenêtre **Manage NuGet Packages.** Assurez-vous que la source de chute dans le coin `nuget.org`supérieur gauche du dialogue est réglé à , de sorte que vous êtes à la recherche du référentiel central de paquet NuGet.

    ![Répertorier les packages NuGet](media/nuget-walkthrough-add-packages1.png)

3. Utilisez la zone de recherche dans le coin supérieur droit pour rechercher un package spécifique, par exemple `EntityFramework`. Une fois que vous avez trouvé un package à utiliser, sélectionnez-le, puis cliquez sur le bouton **Ajouter le package** pour commencer l’installation.

    ![Ajouter entityFramework NuGet Package](media/nuget-walkthrough-add-packages2.png)

4. Une fois le package téléchargé, il est ajouté à votre projet. La solution changera en fonction du type de projet que vous modifiez :

    **Projets Xamarin**
    * Le nœud **Références** contient une liste de tous les assemblys qui font partie d’un package NuGet.
    * Le nœud **Packages** montre chaque package NuGet que vous avez téléchargé. Vous pouvez mettre à jour ou supprimer un package dans cette liste.
    
    **.NET Projets de base**

    * Les **dépendances > nœud NuGet** affiche chaque paquet NuGet que vous avez téléchargé. Vous pouvez mettre à jour ou supprimer un package dans cette liste.

## <a name="using-nuget-packages"></a>Utilisation de packages NuGet

Une fois le package NuGet ajouté et les références du projet mises à jour, vous pouvez programmer en utilisant les API comme vous le feriez avec n’importe quelle référence de projet.

Veillez à ajouter les directives `using` nécessaires en haut de votre fichier :

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Mise à jour des paquets

Les mises à jour du paquet peuvent être effectuées soit tout à la fois, en cliquant à droite sur le nœud **dépendances** **(Nœud de paquets** pour les projets Xamarin), ou individuellement sur chaque paquet. Lorsqu’une nouvelle version d’un package NuGet ![est disponible, une icône de mise à jour apparaît Flèche Up avec cercle](media/nuget-walkthrough-update-icon.png).

Cliquez à droite sur **les dépendances** pour accéder au menu contextuelle et choisir mise à **jour** pour mettre à jour tous les paquets :

![Menu Packages](media/nuget-walkthrough-packages-menu-update.png)

* **Gérer les forfaits NuGet** - Ouvre la fenêtre pour ajouter plus de paquets au projet.
* **Mettre à jour** : recherche les versions les plus récentes des packages sur le serveur source et les télécharge.
* **Restaurer** : télécharge les packages manquants (sans mettre à jour les packages existants vers leur version la plus récente).

Les options Mettre à jour et Restaurer sont également disponibles au niveau de la solution, et elles affectent tous les projets de la solution.

### <a name="locating-outdated-packages"></a>Localiser les paquets périmés
Depuis le bloc-solutions, vous pouvez consulter la version d’un paquet actuellement installé et cliquer à droite sur le paquet à mettre à jour.

![Menu de paquets avec les options de mise à jour, supprimer, rafraîchir](media/nuget-walkthrough-PackageMenu.png)

Vous verrez également une notification à côté du nom du paquet lorsqu’une nouvelle version d’un package est disponible, de sorte que vous pouvez décider si vous pouvez le mettre à jour.

![Notification affichée lorsqu’une nouvelle version de paquet est disponible](media/nuget-walkthrough-package-update-available.png)

Dans le menu indiqué, vous avez deux options :

* **Mettre à jour** : recherche une version plus récente sur le serveur source et si elle existe, la télécharge.
* **Supprimer** : supprime le package de ce projet et supprime les assemblys concernés des références du projet.

## <a name="manage-packages-for-the-solution"></a>Gérer des packages pour la solution

La gestion des packages pour une solution est un moyen pratique de travailler simultanément sur plusieurs projets.

1. Cliquez à droite sur la solution et **sélectionnez Manage NuGet Packages...**:

    ![Gérer les packages NuGet pour la solution](media/nuget-walkthrough-manage-packages-solution.png)

1. Lorsque vous gérez des packages pour la solution, l’interface utilisateur vous permet de sélectionner les projets affectés par les opérations :

    ![Sélecteur de projet lors de la gestion de packages pour la solution](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Onglet Consolider

Lorsque vous travaillez dans une solution avec plusieurs projets, il est considéré comme une pratique exemplaire pour s’assurer que partout où vous utilisez le même paquet NuGet dans chaque projet, vous utilisez également le même numéro de version de ce paquet. Visual Studio pour Mac contribue à faciliter les choses en fournissant un onglet **Consolidate** dans l’interface utilisateur Package Manager lorsque vous choisissez de gérer des paquets pour une solution. À l’aide de cet onglet, vous pouvez facilement voir où les paquets avec des numéros de version distincts sont utilisés par différents projets dans la solution:

![Onglet Consolider de l’interface utilisateur du gestionnaire de package](media/nuget-walkthrough-consolidate-tab.png)

Dans cet exemple, le projet NuGetDemo utilise Microsoft.EntityFrameworkCore 2.20, tandis que NuGetDemo.Shared utilise Microsoft.EntityFrameworkCore 2.2.6. Pour consolider les versions de package, procédez comme suit :

- Sélectionnez les projets à mettre à jour dans la liste des projets.
- Sélectionnez la version à utiliser dans tous ces projets dans la liste **des nouvelles versions,** telles que Microsoft.EntityFrameworkCore 3.0.0.
- Sélectionnez le bouton **Consolidate Package.**

Le gestionnaire de package installe la version de package sélectionnée dans tous les projets sélectionnés, après quoi le package ne s'affiche plus sous l’onglet **Consolider**.

## <a name="adding-package-sources"></a>Ajout de sources de packages

Les colis disponibles à l’installation sont initialement récupérés à partir de nuget.org. Cependant, vous pouvez ajouter d’autres emplacements de paquets à Visual Studio pour Mac. Ceci peut être pratique pour tester vos propres packages NuGet en cours de développement, ou pour utiliser un serveur NuGet privé au sein de votre entreprise ou organisation.

Dans Visual Studio for Mac, naviguez vers **Visual Studio > Préférences > NuGet > Sources** pour afficher et modifier la liste des sources de paquets. Notez que les sources peuvent être un serveur distant (spécifié par une URL) ou un répertoire local.

![Sources de packages](media/nuget-walkthrough-PackageSource.png)

Cliquez sur **Ajouter** pour configurer une nouvelle source. Entrez un nom convivial et l’URL (ou le chemin du fichier) vers la source du package. Si la source est un serveur web sécurisé, entrez le nom d’utilisateur et le mot de passe, sinon laissez ces entrées vides :

![Ajouter des sources de packages](media/nuget-walkthrough-PackageSource2.png)

Vous pouvez sélectionner différentes sources lors de la recherche de packages :

![Ajouter des sources de packages](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Contrôle de version

La documentation de NuGet traite de [l’utilisation de NuGet sans validation des packages auprès de contrôle de code source](/nuget/consume-packages/packages-and-source-control). Si vous préférez ne pas stocker les fichiers binaires et les informations non utilisées dans le contrôle de code source, vous pouvez configurer Visual Studio pour Mac pour restaurer automatiquement les packages à partir du serveur. En d’autres termes, quand un développeur récupère le projet à partir du contrôle de code source pour la première fois, Visual Studio pour Mac télécharge et installe automatiquement les packages nécessaires.

![Restaurer automatiquement les packages](media/nuget-walkthrough-AutoRestore.png)

Pour plus d’informations sur la façon d’exclure le répertoire `packages` du suivi, consultez la documentation spécifique à votre contrôle de code source.

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Voir aussi

* [Installer et utiliser un package dans Visual Studio (sur Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

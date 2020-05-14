---
title: Inclusion d’un package NuGet dans votre projet
description: Ce document explique comment inclure un package NuGet dans un projet Xamarin. Il décrit la recherche et le téléchargement d’un package, et il présente les fonctionnalités d’intégration de l’IDE.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.openlocfilehash: 728a225f4a1d14af986039cae7cb2fc8a493ecc9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983302"
---
# <a name="include-a-nuget-package-in-your-project"></a>Inclure un package NuGet dans votre projet

NuGet est le gestionnaire de packages le plus répandu pour le développement .NET, et il est intégré à Visual Studio pour Mac et à Visual Studio sur Windows. Vous pouvez rechercher et ajouter des packages à vos projets Xamarin.iOS et Xamarin.Android en utilisant l’un ou l’autre de ces IDE.

Cet article explique comment inclure un package NuGet dans un projet. De plus, il présente la chaîne d’outils qui permet d’exécuter le processus sans interruption.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet dans Visual Studio pour Mac

Pour illustrer les fonctionnalités des packages NuGet, nous allons d’abord créer une application et y ajouter un package. Nous présenterons ensuite les fonctionnalités de l’IDE qui aident à gérer les packages.

## <a name="create-a-new-project"></a>Création d'un projet

Pour commencer, créez un projet nommé `HelloNuget`, comme illustré ci-dessous. Cet exemple montre le modèle Application avec affichage unique pour iOS, mais tous les types de projet pris en charge fonctionnent également :

![Créer un projet iOS](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Ajout d’un package

Avec l’ouverture du projet en Visual Studio pour Mac, cliquez à droite sur le dossier **Paquets** dans le **plate-forme de solution** et sélectionnez **Ajouter des paquets**:

![Action contextuelle Ajouter un nouveau package NuGet](media/nuget-walkthrough-PackagesMenu.png)

Cela lance la fenêtre **Add Packages.** Vérifiez que la liste déroulante Source est définie sur `nuget.org` :

![Liste déroulante Source](media/nuget-walkthrough-Source.png)

Lorsque la fenêtre s’ouvre, il charge une liste de paquets à partir de la source de paquet par défaut: nuget.org. Les premiers résultats ressemblent à ceci :

![Répertorier les packages NuGet](media/nuget-walkthrough-AddPackages1.png)

Utilisez la zone de recherche dans le coin supérieur droit pour rechercher un package spécifique, par exemple `azure`. Quand vous avez trouvé un package que vous voulez utiliser, sélectionnez-le et cliquez sur le bouton **Ajouter le package** pour commencer l’installation.

[Ajouter le package NuGet Azure](media/nuget-walkthrough-AddPackages2.png)

Une fois le package téléchargé, il est ajouté à votre projet. La solution est changée comme suit :

* Le nœud **Références** contient une liste de tous les assemblys qui font partie d’un package NuGet.
* Le nœud **Packages** montre chaque package NuGet que vous avez téléchargé. Vous pouvez mettre à jour ou supprimer un package dans cette liste.
* Un fichier **packages.config** sera ajouté au projet. Ce fichier XML est utilisé par l’IDE pour effectuer le suivi des versions du package qui sont référencées dans ce projet. Ce fichier ne doit pas être modifié manuellement, mais vous devez le conserver dans la gestion de versions. Notez qu’un fichier project.json peut être utilisé à la place d’un fichier packages.config. Le fichier project.json est un nouveau format de fichier de package introduit avec NuGet 3, qui prend en charge la restauration transitive. Pour plus d’informations sur project.json, consultez la [documentation de NuGet](/NuGet/Schema/Project-Json). Le fichier project.json doit être ajouté manuellement, et le projet doit être fermé puis rouvert avant que ce fichier soit utilisé dans Visual Studio pour Mac.

## <a name="using-nuget-packages"></a>Utilisation de packages NuGet

Une fois le package NuGet ajouté et les références du projet mises à jour, vous pouvez programmer en utilisant les API comme vous le feriez avec n’importe quelle référence de projet.

Veillez à ajouter les directives `using` nécessaires en haut de votre fichier :

```csharp
using Newtonsoft.Json;
```

La plupart des packages NuGet fournissent des informations supplémentaires, comme un lien vers une page README ou Projet vers la source NuGet. Vous pouvez normalement trouver ce lien dans le texte de présentation du package sur la page Ajouter des packages :

[Lien Afficher la page du projet](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Mises à jour d’un package

Les mises à jour d’un package peuvent être effectuées toutes en même temps en cliquant sur le nœud **Packages**, ou bien individuellement sur chaque composant.

Cliquez avec le bouton droit sur **Packages** pour accéder au menu contextuel :

![Menu Packages](media/nuget-walkthrough-PackagesMenu.png)

* **Ajouter des packages** : ouvre la fenêtre permettant d’ajouter plus de packages au projet.
* **Mettre à jour** : recherche les versions les plus récentes des packages sur le serveur source et les télécharge.
* **Restaurer** : télécharge les packages manquants (sans mettre à jour les packages existants vers leur version la plus récente).

Les options Mettre à jour et Restaurer sont également disponibles au niveau de la solution, et elles affectent tous les projets de la solution.

Vous pouvez aussi cliquer avec le bouton droit sur des packages individuels pour accéder à un menu contextuel :

![Menu Packages](media/nuget-walkthrough-PackageMenu.png)

* **Numéro de version** : le numéro de version est un élément de menu désactivé. Il est fourni uniquement à titre d’information.
* **Mettre à jour** : recherche une version plus récente sur le serveur source et si elle existe, la télécharge.
* **Supprimer** : supprime le package de ce projet et supprime les assemblys concernés des références du projet.

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

---
title: Inclusion d’un package NuGet dans votre projet
description: Ce document explique comment inclure un package NuGet dans un projet à l’aide de Visual Studio pour Mac. Il décrit la recherche et le téléchargement d’un package, et il présente les fonctionnalités d’intégration de l’IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/18/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 55b4691a7adb03d4ee8fd5e05e7bd9d7daa28f13
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213691"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Installer et gérer des packages NuGet dans Visual Studio pour Mac

L’interface utilisateur du gestionnaire de package NuGet dans Visual Studio pour Mac vous permet d’installer, de désinstaller et de mettre à jour facilement des packages NuGet dans des projets et des solutions. Vous pouvez rechercher et ajouter des packages à vos projets .NET Core, ASP.NET Core et Xamarin.

Cet article explique comment inclure un package NuGet dans un projet. De plus, il présente la chaîne d’outils qui permet d’exécuter le processus sans interruption.

Pour une introduction à l’utilisation de NuGet dans Visual Studio pour Mac [, consultez démarrage rapide : Installer et utiliser un package dans Visual Studio pour Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Rechercher et installer un package

1. Avec un projet ouvert dans Visual Studio pour Mac, cliquez avec le bouton droit sur le dossier **dépendances** (dossier**packages** si vous utilisez un projet Xamarin) dans le **panneau solutions** puis sélectionnez **gérer les packages NuGet...** .

    ![Action contextuelle Ajouter un nouveau package NuGet](media/nuget-walkthrough-packages-menu.png)

2. La fenêtre **gérer les packages NuGet** s’ouvre. Vérifiez que la liste déroulante source dans le coin supérieur gauche de la boîte de dialogue `nuget.org`est définie sur.

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

Les mises à jour de package peuvent être effectuées en une seule fois, en cliquant avec le bouton droit sur le nœud **dépendances** (nœud**packages** pour les projets Xamarin) ou individuellement sur chaque package. Quand une nouvelle version d’un package NuGet est disponible, une icône de mise ![à jour s’affiche](media/nuget-walkthrough-update-icon.png)avec un cercle.

Cliquez avec le bouton droit sur **dépendances** pour accéder au menu contextuel, puis choisissez **mettre** à jour pour mettre à jour tous les packages :

![Menu Packages](media/nuget-walkthrough-packages-menu-update.png)

* **Gérer les packages NuGet** : ouvre la fenêtre pour ajouter d’autres packages au projet.
* **Mettre à jour** : recherche les versions les plus récentes des packages sur le serveur source et les télécharge.
* **Restaurer** : télécharge les packages manquants (sans mettre à jour les packages existants vers leur version la plus récente).

Les options Mettre à jour et Restaurer sont également disponibles au niveau de la solution, et elles affectent tous les projets de la solution.

Dans le panneau solutions, vous pouvez afficher la version d’un package actuellement installée et cliquer avec le bouton droit sur le package à mettre à jour.

![Menu packages avec les options de mise à jour, de suppression et d’actualisation](media/nuget-walkthrough-PackageMenu.png)

Vous verrez également une notification en regard du nom du package lorsqu’une nouvelle version d’un package est disponible. vous pouvez donc décider si vous souhaitez la mettre à jour.

![Notification affichée lorsqu’une nouvelle version de package est disponible](media/nuget-walkthrough-package-update-available.png)

Dans le menu qui s’affiche, vous avez deux options :

* **Mettre à jour** : recherche une version plus récente sur le serveur source et si elle existe, la télécharge.
* **Supprimer** : supprime le package de ce projet et supprime les assemblys concernés des références du projet.

## <a name="adding-package-sources"></a>Ajout de sources de packages

Les packages disponibles pour l’installation sont initialement extraits de nuget.org. Cependant, vous pouvez ajouter d’autres emplacements de packages à Visual Studio pour Mac. Ceci peut être pratique pour tester vos propres packages NuGet en cours de développement, ou pour utiliser un serveur NuGet privé au sein de votre entreprise ou organisation.

Dans Visual Studio pour Mac, accédez à **Visual Studio > Préférences > NuGet > Sources** pour voir et modifier la liste des sources de packages. Notez que les sources peuvent être un serveur distant (spécifié par une URL) ou un répertoire local.

![Sources de packages](media/nuget-walkthrough-PackageSource.png)

Cliquez sur **Ajouter** pour configurer une nouvelle source. Entrez un nom convivial et l’URL (ou le chemin du fichier) vers la source du package. Si la source est un serveur web sécurisé, entrez le nom d’utilisateur et le mot de passe, sinon laissez ces entrées vides :

![Ajouter des sources de packages](media/nuget-walkthrough-PackageSource2.png)

Vous pouvez sélectionner différentes sources lors de la recherche de packages :

![Ajouter des sources de packages](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Gestion de version

La documentation de NuGet traite de [l’utilisation de NuGet sans validation des packages auprès de contrôle de code source](/nuget/consume-packages/packages-and-source-control). Si vous préférez ne pas stocker les fichiers binaires et les informations non utilisées dans le contrôle de code source, vous pouvez configurer Visual Studio pour Mac pour restaurer automatiquement les packages à partir du serveur. En d’autres termes, quand un développeur récupère le projet à partir du contrôle de code source pour la première fois, Visual Studio pour Mac télécharge et installe automatiquement les packages nécessaires.

![Restaurer automatiquement les packages](media/nuget-walkthrough-AutoRestore.png)

Pour plus d’informations sur la façon d’exclure le répertoire `packages` du suivi, consultez la documentation spécifique à votre contrôle de code source.

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Voir aussi

* [Installer et utiliser un package dans Visual Studio (sur Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

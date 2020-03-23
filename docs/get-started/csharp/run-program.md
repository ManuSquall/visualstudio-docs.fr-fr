---
title: Comment exécuter un programme C
description: Guide du débutant sur la façon d’exécuter un programme de Cmd dans Visual Studio.
ms.custom: get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ffe52fc2bf7d05084307b4d972e45f4b1d2acdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "76924615"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Comment : Exécuter un programme CMD en studio visuel

Ce que vous devez faire pour exécuter un programme dépend de ce que vous partez, du type de programme, d’application ou de service qu’il est, et de la question de savoir si vous voulez l’exécuter sous le débogé ou non. Dans le cas le plus simple, lorsque vous avez un projet ouvert dans Visual Studio, construisez et exécutez-le en appuyant sur **Ctrl**+**F5** **(Démarrer sans débogage**) ou **F5** (**Commencez par débogage**), ou appuyez sur la flèche verte ( Démarrer**bouton**) sur la barre d’outils principale Visual Studio.

![Capture d’écran affichant le bouton de démarrage](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>À partir d’un projet

Si vous avez un projet C (fichier *.csproj),* alors vous pouvez l’exécuter, s’il s’agit d’un programme runnable. Si un projet contient un `Main` fichier C avec une méthode, et sa sortie est exécutable (EXE), alors très probablement il s’exécutera s’il construit avec succès.

Si vous avez déjà le code de votre programme dans un projet de Visual Studio, ouvrez le projet. Pour ouvrir le projet, double-clic ou appuyez sur le *.csproj* de windows File Explorer, ou de Visual Studio, choisissez **Open un projet**, parcourez pour trouver le projet (*.csproj*) fichier, et choisissez le fichier de projet.

Après les charges des projets dans Visual Studio, appuyez sur **Ctrl**+**F5** (**Démarrer sans débogage**) ou utiliser le bouton **Démarrer** vert sur la barre d’outils Visual Studio pour exécuter le programme.  S’il y a plusieurs `Main` projets, celui avec la méthode doit être défini comme le projet de démarrage. Pour définir le projet de démarrage, cliquez à droite sur un nœud de projet, et choisissez **Set comme projet de démarrage**.

![Définir un projet de démarrage](media/set-as-startup-project.png)

Visual Studio tente de construire et d’exécuter votre projet.  S’il y a des erreurs de construction, vous voyez la sortie de build dans la fenêtre **de sortie** et les erreurs dans la fenêtre de **liste d’erreur.**

Si la version réussit, l’application fonctionne d’une manière appropriée pour le type de projet. Les applications consoles s’exécutent dans une fenêtre terminale, les applications de bureau Windows commencent dans une nouvelle fenêtre, les applications Web commencent dans le navigateur (hébergé par IIS Express), et ainsi de suite.

## <a name="starting-from-code"></a>À partir du code

Si vous partez d’une liste de code, d’un fichier de code ou d’un petit nombre de fichiers, assurez-vous d’abord que le code que vous souhaitez exécuter provient d’une source fiable et qu’il s’agit d’un programme runnable. S’il `Main` a une méthode, il est probablement destiné comme un programme runnable que vous pouvez utiliser le modèle Console App pour créer un projet pour travailler avec elle dans Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Liste de code pour un seul fichier

Démarrer Visual Studio, ouvrir un projet de console C vide, sélectionner tout le code dans le fichier .cs qui est déjà dans le projet, et le supprimer. Ensuite, collez le contenu de votre code dans le fichier .cs. Lorsque vous collez le code, surcriez ou supprimez le code qui était là avant. Renommer le fichier pour correspondre au code d’origine.

### <a name="code-listings-for-a-few-files"></a>Listes de code pour quelques fichiers

Démarrer Visual Studio, ouvrir un projet de console C vide, sélectionner tout le code dans le fichier .cs qui est déjà dans le projet, et le supprimer. Ensuite, coller le contenu du premier fichier de code dans le fichier .cs. Renommer le fichier pour correspondre au code d’origine. 

Pour un deuxième fichier, cliquez à droite sur le nœud de projet dans **Solution Explorer** pour ouvrir le menu raccourci pour le projet, et choisissez Ajouter > **élément existant** (ou utiliser la combinaison clé **Shift**+**Alt**+**A**), et sélectionnez les fichiers de code.

### <a name="multiple-files-on-disk"></a>Fichiers multiples sur disque

1. Créez un nouveau projet du type approprié (utilisez **l’application console** C si vous n’êtes pas sûr).

2. Cliquez à droite sur le nœud de projet, s’ajouter **Add** > **à l’élément existant** pour sélectionner les fichiers et les importer dans votre projet.  

### <a name="starting-from-a-folder"></a>À partir d’un dossier

Lorsque vous travaillez avec un dossier de nombreux fichiers, voyez d’abord s’il y a un projet ou une solution.  Si le programme a été créé avec Visual Studio, vous devez trouver un fichier de projet ou un fichier de solution. Recherchez des fichiers avec l’extension *.csproj* ou l’extension .sln et dans le Windows File Explorer, double-cliquez sur l’un d’eux pour les ouvrir dans Visual Studio. Voir [À partir d’une solution ou d’un projet Visual Studio](#starting-from-a-project).

Si vous n’avez pas de fichier de projet, comme si le code a été développé dans un autre environnement de développement, puis ouvrez le dossier de haut niveau en utilisant la méthode **du dossier Open** dans Visual Studio. Voir [Développer le code sans projets ni solutions](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>À partir d’un GitHub ou Azure DevOps repo

Si le code que vous souhaitez exécuter est dans GitHub ou dans un repo Azure DevOps, vous pouvez utiliser Visual Studio pour ouvrir le projet directement à partir de la pension. Voir [Ouvrez un projet à partir d’une pension](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Exécuter le programme

Pour commencer le programme, appuyez sur la flèche verte (bouton**Démarrer)** sur la barre d’outils visual Studio principale, ou appuyez sur **F5** ou **Ctrl**+**F5** pour exécuter le programme. Lorsque vous utilisez le bouton **Démarrer,** il s’exécute sous le débailleur.  Visual Studio tente de construire le code dans votre projet et de l’exécuter.  Si ça réussit, super ! Mais si ce n’est pas le cas, continuez à lire pour quelques idées sur la façon de le faire construire avec succès.

## <a name="troubleshooting"></a>Dépannage

Votre code peut avoir des erreurs, mais si le code est correct, mais dépend juste de certains autres assemblages ou paquets NuGet, ou a été écrit pour cibler une version différente de .NET, vous pourriez être en mesure de le réparer facilement.

### <a name="add-references"></a>Ajouter des références

Pour construire correctement, le code doit être correct et avoir les bonnes références mises en place aux bibliothèques ou à d’autres dépendances. Vous pouvez regarder les lignes rouges squiggly et à la **liste d’erreurs** pour voir si le programme a des erreurs, avant même de le compiler et de l’exécuter. Si vous constatez des erreurs liées à des noms non résolus, vous devez probablement ajouter une référence ou une directive utilisant, ou les deux. Si le code fait référence à des assemblages ou à des paquets NuGet, vous devez ajouter ces références dans le projet.

Visual Studio tente de vous aider à identifier les références manquantes. Lorsqu’un nom n’est pas résolu, une icône d’ampoule apparaît dans l’éditeur. Si vous cliquez sur l’ampoule, vous pouvez voir quelques suggestions sur la façon de résoudre le problème. Les correctifs pourraient être à:

- ajouter une directive à l’aide
- ajouter une référence à une assemblée, ou
- installer un paquet NuGet.

#### <a name="missing-using-directive"></a>Absence de directive

Par exemple, dans l’écran suivant, `using System;` vous pouvez choisir d’ajouter au `Console`début du fichier de code pour résoudre le nom non résolu :

![Capture d’écran de l’ampoule pour ajouter une directive à l’aide](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Référence d’assemblage manquante

.Net références peuvent être sous la forme d’assemblages ou de paquets NuGet. Habituellement, si vous trouvez du code source, l’éditeur ou l’auteur expliquera les assemblages requis et les paquets dont dépend le code. Pour ajouter une référence à un projet manuellement, cliquez à droite sur le nœud **Références** dans le **Solution Explorer**, choisissez **Ajouter référence**et localiser l’assemblage requis.

![Capture d’écran du menu Add Reference](media/add-reference.png)

Vous pouvez trouver des assemblages et ajouter des références en suivant les instructions dans Ajouter ou supprimer les références en [utilisant le gestionnaire de référence](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Paquet NuGet manquant

Si Visual Studio détecte un paquet NuGet manquant, une ampoule apparaît et vous donne la possibilité de l’installer :

![Capture d’écran de l’ampoule pour installer le paquet](media/lightbulb-add-package.png)

Si cela ne résout pas le problème et Visual Studio ne peut pas localiser le paquet, essayez de le rechercher en ligne. Voir [Installer et utiliser un forfait NuGet dans Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Utilisez la bonne version de .NET

Étant donné que différentes versions du cadre .NET ont un certain degré de compatibilité rétrograde, un cadre plus récent pourrait exécuter le code écrit pour un cadre plus ancien sans aucune modification. Mais, parfois, vous devez cibler un cadre spécifique. Vous devrez peut-être installer une version spécifique du cadre .NET ou .NET Core, si elle n’est pas déjà installée. Voir [Modifier Visual Studio](../../install/modify-visual-studio.md).

Pour modifier le cadre cible, voir [Modifier le cadre cible](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Pour plus d’informations, voir [Fautes de ciblage .NET Framework .NET.](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)

## <a name="next-steps"></a>Étapes suivantes

Explorez l’environnement de développement Visual Studio en lisant [Bienvenue au Visual Studio IDE](../visual-studio-ide.md).

## <a name="see-also"></a>Voir aussi

[Créer votre première application C#](tutorial-console.md)

---
title: Comment exécuter un programme (C#)
description: Guide du débutant sur l’exécution d’un programme C# dans Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e20caabb55e65801224177168f5c936f81402bbd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385225"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Comment : exécuter un programme C# dans Visual Studio

Ce que vous devez faire pour exécuter un programme dépend de ce que vous démarrez, du type de programme, de l’application ou du service dont il s’agit et de la nécessité ou non de l’exécuter sous le débogueur. Dans le cas le plus simple, quand un projet est ouvert dans Visual Studio, générez-le et exécutez-le en appuyant sur **CTRL** + **F5** (**exécuter sans débogage**) ou **F5** (**Démarrer avec le débogage**) ou appuyez sur la flèche verte (**bouton Démarrer**) de la barre d’outils principale de Visual Studio.

![Capture d’écran montrant le bouton Démarrer](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Démarrage à partir d’un projet

Si vous avez un projet C# (fichier *. csproj* ), vous pouvez l’exécuter, s’il s’agit d’un programme exécutable. Si un projet contient un fichier C# avec une `Main` méthode et que sa sortie est un fichier exécutable (exe), il s’exécutera probablement s’il est généré avec succès.

Si vous disposez déjà du code pour votre programme dans un projet dans Visual Studio, ouvrez le projet. Pour ouvrir le projet, double-cliquez ou appuyez sur le fichier *. csproj* dans l’Explorateur de fichiers Windows, ou dans Visual Studio, choisissez **ouvrir un projet**, recherchez le fichier projet (*. csproj*) et choisissez le fichier projet.

Une fois que les projets se chargent dans Visual Studio, appuyez sur **CTRL** + **F5** (**exécuter sans débogage**) ou utilisez le bouton **Démarrer** vert dans la barre d’outils de Visual Studio pour exécuter le programme.  S’il y a plusieurs projets, celui avec la `Main` méthode doit être défini comme projet de démarrage. Pour définir le projet de démarrage, cliquez avec le bouton droit sur un nœud de projet, puis choisissez **définir comme projet de démarrage**.

![Définir le projet de démarrage](media/set-as-startup-project.png)

Visual Studio tente de générer et d’exécuter votre projet.  Si des erreurs de build se produisent, la sortie de génération s’affiche dans la fenêtre **sortie** et les erreurs dans la fenêtre **liste d’erreurs** .

Si la génération est réussie, l’application s’exécute de manière appropriée pour le type de projet. Les applications de console s’exécutent dans une fenêtre de terminal, les applications de bureau Windows démarrent dans une nouvelle fenêtre, les applications Web démarrent dans le navigateur (hébergé par IIS Express), et ainsi de suite.

## <a name="starting-from-code"></a>À partir du code

Si vous démarrez à partir d’une liste de code, d’un fichier de code ou d’un petit nombre de fichiers, assurez-vous d’abord que le code que vous souhaitez exécuter provient d’une source fiable et qu’il s’agit d’un programme exécutable. S’il possède une `Main` méthode, il est probablement conçu comme un programme exécutable que vous pouvez utiliser avec le modèle d’application console pour créer un projet à utiliser dans Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Liste de code pour un seul fichier

Démarrez Visual Studio, ouvrez un projet de console C# vide, sélectionnez tout le code dans le fichier. cs qui se trouve déjà dans le projet, puis supprimez-le. Collez ensuite le contenu de votre code dans le fichier. cs. Lorsque vous collez le code, remplacez ou supprimez le code qui était auparavant. Renommez le fichier pour qu’il corresponde au code d’origine.

### <a name="code-listings-for-a-few-files"></a>Listes de code pour quelques fichiers

Démarrez Visual Studio, ouvrez un projet de console C# vide, sélectionnez tout le code dans le fichier. cs qui se trouve déjà dans le projet, puis supprimez-le. Collez ensuite le contenu du premier fichier de code dans le fichier. cs. Renommez le fichier pour qu’il corresponde au code d’origine. 

Pour un deuxième fichier, cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** pour ouvrir le menu contextuel du projet, puis choisissez **Ajouter > élément existant** (ou utilisez la combinaison de touches **MAJ** + **ALT** + **a**), puis sélectionnez les fichiers de code.

### <a name="multiple-files-on-disk"></a>Plusieurs fichiers sur le disque

1. Créez un nouveau projet de type approprié (utilisez l' **application console** C# si vous n’en êtes pas sûr).

2. Cliquez avec le bouton droit sur le nœud du projet, se **Ajouter** un  >  **élément existant** pour sélectionner les fichiers et les importer dans votre projet.  

### <a name="starting-from-a-folder"></a>Démarrage à partir d’un dossier

Lorsque vous utilisez un dossier contenant de nombreux fichiers, commencez par vérifier s’il existe un projet ou une solution.  Si le programme a été créé avec Visual Studio, vous devez trouver un fichier projet ou un fichier solution. Recherchez les fichiers portant l’extension *. csproj* ou. sln et, dans l’Explorateur de fichiers Windows, double-cliquez sur l’un d’eux pour les ouvrir dans Visual Studio. Consultez [Démarrer à partir d’une solution ou d’un projet Visual Studio](#starting-from-a-project).

Si vous n’avez pas de fichier projet, par exemple si le code a été développé dans un autre environnement de développement, ouvrez le dossier de niveau supérieur à l’aide de la méthode **ouvrir le dossier** dans Visual Studio. Consultez [développer du code sans projets ni solutions](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>Démarrage à partir d’un GitHub ou d’Azure DevOps référentiel

Si le code que vous souhaitez exécuter se trouve dans GitHub ou dans un référentiel Azure DevOps, vous pouvez utiliser Visual Studio pour ouvrir le projet directement à partir du référentiel. Consultez [ouvrir un projet à partir d’un référentiel](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Exécuter le programme

Pour démarrer le programme, appuyez sur la flèche verte (bouton **Démarrer** ) de la barre d’outils principale de Visual Studio, ou appuyez sur **F5** ou sur **CTRL** + **F5** pour exécuter le programme. Quand vous utilisez le bouton **Démarrer** , il s’exécute sous le débogueur.  Visual Studio tente de générer le code dans votre projet et de l’exécuter.  Si cela fonctionne, parfait ! Mais si ce n’est pas le cas, poursuivez la lecture pour obtenir des idées sur la manière de réussir la génération.

## <a name="troubleshooting"></a>Dépannage

Votre code peut contenir des erreurs, mais si le code est correct, mais dépend simplement d’autres assemblys ou packages NuGet, ou a été écrit pour cibler une version différente de .NET, vous pouvez peut-être le corriger facilement.

### <a name="add-references"></a>Ajouter des références

Pour générer correctement, le code doit être correct et les références appropriées doivent être configurées pour les bibliothèques ou d’autres dépendances. Vous pouvez examiner les lignes ondulées rouges et au **liste d’erreurs** pour voir si le programme comporte des erreurs, même avant de le compiler et de l’exécuter. Si vous rencontrez des erreurs liées à des noms non résolus, vous devrez probablement ajouter une référence ou une directive using, ou les deux. Si le code fait référence à des assemblys ou des packages NuGet, vous devez ajouter ces références dans le projet.

Visual Studio tente de vous aider à identifier les références manquantes. Lorsqu’un nom n’est pas résolu, une icône d’ampoule s’affiche dans l’éditeur. Si vous cliquez sur l’ampoule, vous pouvez voir des suggestions sur la façon de résoudre le problème. Les correctifs peuvent être les suivants :

- Ajouter une directive using
- Ajoutez une référence à un assembly, ou
- Installez un package NuGet.

#### <a name="missing-using-directive"></a>Directive using manquante

Par exemple, dans l’écran suivant, vous pouvez choisir d’ajouter `using System;` au début du fichier de code pour résoudre le nom non résolu `Console` :

![Capture d’écran de l’ampoule pour ajouter une directive using](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Référence d’assembly manquante

Les références .NET peuvent se présenter sous la forme d’assemblys ou de packages NuGet. En règle générale, si vous trouvez du code source, le serveur de publication ou l’auteur explique les assemblys requis et les packages dont le code dépend. Pour ajouter manuellement une référence à un projet, cliquez avec le bouton droit sur le nœud **références** dans le **Explorateur de solutions**, choisissez **Ajouter une référence**, puis recherchez l’assembly requis.

![Capture d’écran du menu Ajouter une référence](media/add-reference.png)

Vous pouvez rechercher des assemblys et ajouter des références en suivant les instructions fournies dans [Ajouter ou supprimer des références à l’aide du gestionnaire](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)de références.

#### <a name="missing-nuget-package"></a>Package NuGet manquant

Si Visual Studio détecte un package NuGet manquant, une ampoule s’affiche et vous donne la possibilité de l’installer :

![Capture d’écran de l’ampoule pour installer le package](media/lightbulb-add-package.png)

Si cela ne résout pas le problème et que Visual Studio ne peut pas localiser le package, essayez de le Rechercher en ligne. Consultez [installer et utiliser un package NuGet dans Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Utiliser la version appropriée de .NET

Étant donné que les différentes versions de la .NET Framework ont un certain degré de compatibilité descendante, un Framework plus récent peut exécuter du code écrit pour une infrastructure plus ancienne sans aucune modification. Toutefois, vous devez parfois cibler un Framework spécifique. Vous devrez peut-être installer une version spécifique du .NET Framework ou de .NET Core, si elle n’est pas déjà installée. Consultez [modifier Visual Studio](../../install/modify-visual-studio.md).

Pour modifier la version cible du .NET Framework, consultez [modifier la version cible du .NET Framework](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Pour plus d’informations, consultez [dépannage .NET Framework erreurs de ciblage](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Étapes suivantes

Explorez l’environnement de développement Visual Studio en lisant [Bienvenue dans l’IDE de Visual Studio](../visual-studio-ide.md).

## <a name="see-also"></a>Voir aussi

[Créer votre première application C#](tutorial-console.md)

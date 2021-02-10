---
title: Filtres de solution dans MSBuild
description: Explique les filtres de solution et montre comment générer un fichier de filtre de solution avec MSBuild.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4a5c764ad9ea4190df5e533926671dbd88c53b8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937834"
---
# <a name="solution-filters-in-msbuild"></a>Filtres de solution dans MSBuild

Les fichiers de filtre de solution sont des fichiers JSON avec l’extension *. slnf* qui indiquent les projets à générer ou charger à partir de tous les projets d’une solution. À compter de MSBuild 16,7, vous pouvez appeler MSBuild sur le fichier de filtre de la solution pour générer la solution avec filtrage activé. 

> [!NOTE]
> Le fichier de filtre de la solution réduit l’ensemble des projets qui seront chargés ou générés, et qui simplifie le format. Le fichier solution est toujours requis.

## <a name="build-a-solution-filter-from-the-command-line"></a>Créer un filtre de solution à partir de la ligne de commande

La création d’un fichier de filtre de solution à partir de la ligne de commande utilise exactement la même syntaxe que la génération d’un fichier solution. Spécifiez le fichier de filtre de la solution au lieu de la solution à générer avec le filtrage activé, comme suit :

```console
msbuild [options] solutionFilterFile.slnf
```

Vous pouvez également ajouter des commutateurs et des propriétés supplémentaires comme d’habitude. Consultez [référence de la ligne de commande MSBuild](msbuild-command-line-reference.md). Cette commande génère les projets filtrés et tous les projets dont ils dépendent. Lors de la génération d’un filtre de solution à partir de la ligne de commande, MSBuild suit automatiquement les dépendances. Il génère un projet s’il est spécifié dans le filtre ou référencé par un projet généré.

## <a name="solution-filter-files"></a>Fichiers de filtre de solution

Vous pouvez utiliser Visual Studio pour travailler avec des fichiers de filtre de solution. L’ouverture d’un filtre de solution dans Visual Studio affiche les projets déchargés, ainsi que les projets chargés, et vous donne la possibilité de charger plus de projets pour les sélectionner pour la génération. Vous pouvez charger tous les projets dont le ou les projets initiaux dépendent pour une génération, mais cela n’est pas obligatoire. Consultez [solutions filtrées](../ide/filtered-solutions.md).

Le filtre de la solution n’a pas besoin d’être dans le même dossier que la solution. Le chemin d’accès au fichier solution est relatif à l’emplacement du fichier de filtre de la solution, mais les chemins d’accès à chaque projet sont relatifs au fichier solution lui-même et doivent correspondre aux chemins d’accès du projet dans le fichier solution. L’exemple suivant illustre l’utilisation de chemins d’accès relatifs :

```json
{
  "solution": {
    "path": "..\\..\\Documents\\GitHub\\msbuild\\MSBuild.sln",
    "projects": [
      "src\\Build.OM.UnitTests\\Microsoft.Build.Engine.OM.UnitTests.csproj"
    ]
  }
}
```

Les barres obliques inverses dans les chemins d’accès doivent être doublées, car elles sont placées dans une séquence d’échappement.

## <a name="example"></a>Exemple

Voici un exemple de solution filtrée dans Visual Studio :

![Capture d’écran de la solution filtrée dans Visual Studio](media/solution-with-filter.png)

Dans cette solution, ClassLibrary1 est utilisé à la fois par ProjectA et le projetb. ClassLibrary1 est alors listé comme une référence de projet.

Voici le fichier de filtre de solution généré par Visual Studio :

```json
{
  "solution": {
    "path": "MyApplication.sln",
    "projects": [
      "MyApplication\\MyApplication.csproj",
      "ProjectA\\ProjectA.csproj"
    ]
  }
}
```

Dans cet exemple, quand vous générez avec le filtrage activé (à l’aide de la commande `MSBuild [options] MyFilter.slnf` ), MSBuild génère MyApplication et ProjectA, car ils sont explicitement listés dans le fichier de filtre de la solution. Dans le cadre de la génération de ProjectA, MSBuild génère ClassLibrary1, car ProjectA en dépend.  Le projetb n’est pas généré. (Cette discussion suppose une génération propre. Si des projets ont été générés précédemment, les règles habituelles s’appliquent aux projets ignorés qui sont déjà à jour.)

## <a name="see-also"></a>Voir aussi

- [Solutions filtrées](../ide/filtered-solutions.md)
- [Référence de la ligne de commande MSBuild](msbuild-command-line-reference.md)

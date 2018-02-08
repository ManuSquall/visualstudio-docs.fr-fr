---
title: Personnaliser votre build | Microsoft Docs
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: 
author: kempb
ms.author: kempb
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 82b7503b937babd81a41136656d75c95e844b94c
ms.sourcegitcommit: 062795f922e7b59fe00d3d95a01a9a8a28840017
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2018
---
# <a name="customize-your-build"></a>Personnaliser votre build
Dans les versions de MSBuild antérieures à la version 15, si vous souhaitiez fournir une nouvelle propriété personnalisée aux projets de votre solution, vous deviez ajouter manuellement une référence à cette propriété pour chaque fichier projet de la solution. Ou vous deviez définir la propriété dans un fichier *.props*, puis importer explicitement le fichier *.props* dans chaque projet de la solution, entre autres.

Maintenant, vous pouvez ajouter une nouvelle propriété à chaque projet en une seule étape en la définissant dans un seul fichier appelé *Directory.Build.props* qui se trouve à la racine de votre référentiel. Quand MSBuild s’exécute, *Microsoft.Common.props* recherche le fichier *Directory.Build.props* dans votre structure de répertoire (et *Microsoft.Common.targets* recherche *Directory.Build.targets*). S’il en trouve un, il importe la propriété. *Directory.Build.props* est un fichier défini par l’utilisateur qui fournit des personnalisations aux projets situés dans un répertoire.

## <a name="directorybuildprops-example"></a>Exemple avec Directory.Build.props
Par exemple, si vous souhaitez permettre à l’ensemble de vos projets d’accéder à la nouvelle fonctionnalité Roslyn **/deterministic** (qui est exposée dans la cible `CoreCompile` de Roslyn par la propriété `$(Deterministic)`), vous pouvez procéder comme suit.

1. Créez un nouveau fichier à la racine de votre référentiel appelé *Directory.Build.props*.
2. Ajoutez le code XML suivant au fichier.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Exécutez MSBuild. Les importations existantes de votre projet de *Microsoft.Common.props* et *Microsoft.Common.targets* trouvent le fichier et l’importent.

## <a name="search-scope"></a>Étendue de la recherche
Lorsque vous recherchez un fichier *Directory.Build.props*, MSBuild remonte dans la structure de répertoire par rapport à l’emplacement de votre projet (`$(MSBuildProjectFullPath)`) et s’arrête après avoir localisé un fichier *Directory.Build.props*. Par exemple, si votre `$(MSBuildProjectFullPath)` était *c:\users\username\code\test\case1*, MSBuild commencerait à rechercher ici, puis remonterait dans la structure de répertoire jusqu’à ce qu’il trouve un fichier *Directory.Build.props*, comme dans la structure de répertoire suivante.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
L’emplacement du fichier solution est sans importance pour *Directory.Build.props*.

## <a name="import-order"></a>Ordre d’importation

*Directory.Build.props* est importé très tôt dans *Microsoft.Common.props*, donc les propriétés définies ultérieurement ne sont pas disponibles pour ce dernier. Par conséquent, évitez de faire référence aux propriétés qui ne sont pas encore définies (et qui seront évaluées comme vides).

*Directory.Build.targets* est importé à partir de *Microsoft.Common.targets* après l’importation des fichiers *.targets* à partir des packages NuGet. Il peut donc être utilisé pour remplacer les propriétés et les cibles définies dans la quasi-totalité de la logique de build. Dans certains cas toutefois, il peut être nécessaire d’effectuer des personnalisations dans le fichier projet après l’importation finale.

## <a name="use-case-multi-level-merging"></a>Cas d’utilisation : Fusion à plusieurs niveaux

Supposons que vous ayez la structure de solution standard suivante :

````
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
````

Il peut être souhaitable d’avoir des propriétés communes pour tous les projets *(1)*, des propriétés communes pour les projets *src* *(2-src)* et des propriétés communes pour les projets *test* *(2-test)*.

Pour que MSBuild fusionne correctement les fichiers « internes » (*2-src* et *2-test*) avec le fichier « externe » (*1*), vous devez prendre en compte le fait qu’une fois que MSBuild a trouvé un fichier *Directory.Build.props*, il arrête sa recherche. Pour poursuivre la recherche et fusionner les fichiers internes avec le fichier externe, placez ce qui suit dans les deux fichiers internes :

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Voici un résumé de l’approche générale MSBuild :

- Pour un projet donné, MSBuild recherche le premier *Directory.Build.props* vers le haut de la structure de la solution, le fusionne avec les valeurs par défaut et arrête la recherche
- Si vous souhaitez rechercher et fusionner plusieurs niveaux, importez ([`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove), ci-dessus) le fichier « externe » à partir du fichier « interne ».
- Si le fichier « externe » n’importe pas également un élément situé au-dessus, la recherche s’arrête.
- Pour contrôler le processus de recherche et de fusion, utilisez `$(DirectoryBuildPropsPath)` et `$(ImportDirectoryBuildProps)`.

Ou plus simplement : MSBuild s’arrête au premier *Directory.Build.props* qui n’importe aucun élément.

## <a name="see-also"></a>Voir aussi  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)   

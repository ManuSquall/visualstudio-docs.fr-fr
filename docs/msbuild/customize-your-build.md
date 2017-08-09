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
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: 86f7fef0365a47e8ea88bc3fc46cb0016efd4628
ms.contentlocale: fr-fr
ms.lasthandoff: 06/15/2017

---
# <a name="customize-your-build"></a>Personnaliser votre build
Dans les versions de MSBuild antérieures à la version 15, si vous souhaitiez fournir une nouvelle propriété personnalisée aux projets de votre solution, vous deviez ajouter manuellement une référence à cette propriété pour chaque fichier projet de la solution. Ou vous deviez définir la propriété dans un fichier .props, puis importer explicitement le fichier .props dans chaque projet de la solution, entre autres.

Maintenant, vous pouvez ajouter une nouvelle propriété à chaque projet en une seule étape en la définissant dans un seul fichier appelé Directory.Build.props qui se trouve à la racine de votre référentiel. Quand MSBuild s’exécute, Microsoft.Common.props recherche le fichier Directory.Build.props dans votre structure de répertoire (et Microsoft.Common.targets recherche Directory.Build.targets). S’il en trouve un, il importe la propriété. Directory.Build.props est un fichier défini par l’utilisateur qui fournit des personnalisations aux projets situés dans un répertoire.

## <a name="directorybuildprops-example"></a>Exemple avec Directory.Build.props
Par exemple, si vous souhaitez permettre à l’ensemble de vos projets d’accéder à la nouvelle fonctionnalité Roslyn **/deterministic** (qui est exposée dans la cible CoreCompile de Roslyn par la propriété `$(Deterministic)`), vous pouvez procéder comme suit.

1. Créez un nouveau fichier à la racine de votre référentiel appelé Directory.Build.props.
2. Ajoutez le code XML suivant au fichier.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Exécutez MSBuild. Les importations existantes de votre projet de Microsoft.Common.props et Microsoft.Common.targets trouvent le fichier et l’importent.

## <a name="search-scope"></a>Étendue de la recherche
Lorsque vous recherchez un fichier Directory.Build.props, MSBuild remonte dans la structure de répertoire par rapport à l’emplacement de votre projet ($(MSBuildProjectFullPath)) et s’arrête après avoir localisé un fichier Directory.Build.props. Par exemple, si votre $(MSBuildProjectFullPath) était c:\users\username\code\test\case1, MSBuild commencerait à rechercher ici, puis remonterait dans la structure de répertoire jusqu'à ce qu’il trouve un fichier Directory.Build.props, comme dans la structure de répertoire suivante.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
L’emplacement du fichier solution est sans importance pour Directory.Build.props.

## <a name="import-order"></a>Ordre d’importation

Directory.Build.props est importé très tôt dans Microsoft.Common.props, donc les propriétés définies ultérieurement ne sont pas disponibles pour ce dernier. Par conséquent, évitez de faire référence aux propriétés qui ne sont pas encore définies (et qui seront évaluées comme vides).

Directory.Build.targets est importé à partir de Microsoft.Common.targets après l’importation des fichiers .targets à partir des packages NuGet. Il peut donc être utilisé pour remplacer les propriétés et les cibles définies dans la quasi-totalité de la logique de build. Dans certains cas toutefois, il peut être nécessaire d’effectuer des personnalisations dans le fichier projet après l’importation finale.

## <a name="see-also"></a>Voir aussi  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)   


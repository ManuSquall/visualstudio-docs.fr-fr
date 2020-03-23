---
title: Élément Import (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d9e66934015c7c4a57c7d7c6911b9ebe02ac536
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094492"
---
# <a name="import-element-msbuild"></a>Import, élément (MSBuild)

Importe le contenu d’un fichier projet dans un autre fichier projet.

\<Project> \<Import>

## <a name="syntax"></a>Syntaxe

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Project`|Attribut requis.<br /><br /> Chemin du fichier projet à importer. Le chemin peut inclure des caractères génériques. Les fichiers correspondants sont importés dans un ordre trié. Cette fonctionnalité vous permet d’ajouter du code à un projet simplement en ajoutant le fichier de code dans un répertoire.|
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|
|`Sdk`| Attribut facultatif.<br /><br /> Référence un SDK de projet.|

### <a name="child-elements"></a>Éléments enfants

 None

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| - | - |
| [Projet](../msbuild/project-element-msbuild.md) | Élément racine requis d’un fichier de projet MSBuild. |
| [ImportGroup](../msbuild/importgroup-element.md) | Contient une collection d’éléments `Import` regroupés sous une condition facultative. |

## <a name="remarks"></a>Notes 

 L’élément `Import` vous permet de réutiliser du code commun à de nombreux fichiers projet. Cela facilite la maintenance du code, car les mises à jour que vous apportez au code partagé sont propagées à tous les projets qui l’importent.

 Par convention, les fichiers de projets importés partagés sont enregistrés sous forme de fichiers *.cibles,* mais il s’œd de fichiers de projets MSBuild standard. MSBuild ne vous empêche pas d’importer un projet qui a une extension de nom de fichier différente, mais nous vous recommandons d’utiliser l’extension *.targets* pour la cohérence.

 Les voies relatives dans les projets importés sont interprétées par rapport à l’annuaire du projet d’importation (à quelques exceptions près décrites plus loin dans ce paragraphe). Ainsi, si un fichier projet est importé dans plusieurs fichiers projet à différents emplacements, les chemins relatifs dans le fichier projet importé sont interprétés différemment pour chaque projet importé. Il y a deux exceptions. Une exception est `Import` que dans les éléments, le chemin `Import` est toujours interprété par rapport au projet qui contient l’élément. Une autre exception `UsingTask` est que le toujours `AssemblyFile` interprète le chemin relatif `UsingTask` pour l’attribut par rapport au fichier qui contient l’élément.

 Toutes les propriétés réservées MSBuild qui `MSBuildProjectDirectory` se `MSBuildProjectFile`rapportent au dossier du projet, par exemple, et, qui sont référencées dans un projet importé sont attribués des valeurs basées sur le fichier du projet d’importation.

 Si le projet importé n’a pas d’attribut `DefaultTargets` , les projets importés sont inspectés dans l’ordre dans lequel ils sont importés, et la valeur du premier attribut `DefaultTargets` découvert est utilisée. Par exemple, si ProjectA importe ProjectB et ProjectC (dans cet ordre), et que `DefaultTargets` les importations du ProjectB sont projetées, MSBuild recherche d’abord des éléments précis sur ProjectA, puis ProjectB, puis ProjectD, et enfin ProjectC.

 Le schéma d’un projet importé est identique à celui d’un projet standard. Bien que MSBuild puisse être en mesure de construire un projet importé, il est peu probable qu’un projet importé ne contienne généralement pas d’information sur les propriétés à établir ou l’ordre dans lequel exécuter des cibles. Le projet importé dépend du projet dans lequel il est importé pour fournir ces informations.

## <a name="wildcards"></a>Caractères génériques

 Dans le .NET Framework 4, MSBuild autorise les caractères génériques dans l’attribut de projet. Quand il existe des caractères génériques, toutes les correspondances trouvées sont triées (à des fins de reproductibilité), puis elles sont importées dans cet ordre comme si celui-ci avait été défini explicitement.

 Cela est utile si vous souhaitez offrir un point d’extensibilité pour que quelqu’un d’autre puisse importer un fichier sans avoir à ajouter explicitement le nom du fichier au fichier d’importation. À cette fin, *Microsoft.Common.Targets* contient la ligne suivante en haut du fichier.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a> Exemple

 L’exemple suivant montre un projet qui a plusieurs éléments et propriétés, et qui importe un fichier projet général.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <resourcefile>Strings.resx</resourcefile>

        <compiledresources>
            $(O)\$(MSBuildProjectName).Strings.resources
        </compiledresources>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" />

        <Reference Include="System" />
        <Reference Include="System.Data" />
    </ItemGroup>

    <Import Project="$(CommonLocation)\General.targets" />
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de fichier de projet](../msbuild/msbuild-project-file-schema-reference.md)
- [Comment : Utiliser la même cible dans plusieurs fichiers de projet](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)

---
title: Élément Import (MSBuild) | Microsoft Docs
description: Découvrez comment MSBuild utilise l’élément import pour importer le contenu d’un fichier projet dans un autre fichier projet.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d5a5650402655f4a5a2a0388ac0e57a0b903bc2e
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903957"
---
# <a name="import-element-msbuild"></a>Import, élément (MSBuild)

Importe le contenu d’un fichier projet dans un autre fichier projet.

\<Project>
\<Import>

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

 Aucun

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| - | - |
| [Projet](../msbuild/project-element-msbuild.md) | Élément racine requis d’un fichier projet MSBuild. |
| [ImportGroup](../msbuild/importgroup-element.md) | Contient une collection d’éléments `Import` regroupés sous une condition facultative. |

## <a name="remarks"></a>Notes

 L’élément `Import` vous permet de réutiliser du code commun à de nombreux fichiers projet. Cela facilite la maintenance du code, car les mises à jour que vous apportez au code partagé sont propagées à tous les projets qui l’importent.

 Par Convention, les fichiers projet importés partagés sont enregistrés en tant que fichiers *. targets* , mais il s’agit de fichiers projet MSBuild standard. MSBuild ne vous empêche pas d’importer un projet ayant une extension de nom de fichier différente, mais nous vous recommandons d’utiliser l’extension *. targets* pour des fins de cohérence.

 Les chemins d’accès relatifs dans les projets importés sont interprétés par rapport au répertoire du projet importateur (avec quelques exceptions décrites plus loin dans ce paragraphe). Ainsi, si un fichier projet est importé dans plusieurs fichiers projet à différents emplacements, les chemins relatifs dans le fichier projet importé sont interprétés différemment pour chaque projet importé. Il existe deux exceptions. Une exception est que dans `Import` les éléments, le chemin d’accès est toujours interprété par rapport au projet qui contient l' `Import` élément. Une autre exception est que le `UsingTask` interprète toujours le chemin d’accès relatif de l' `AssemblyFile` attribut par rapport au fichier qui contient l' `UsingTask` élément.

 Toutes les propriétés réservées MSBuild relatives au fichier projet, par exemple, `MSBuildProjectDirectory` et `MSBuildProjectFile` , qui sont référencées dans un projet importé sont affectées de valeurs basées sur le fichier projet d’importation.

 Si le projet importé n’a pas d’attribut `DefaultTargets` , les projets importés sont inspectés dans l’ordre dans lequel ils sont importés, et la valeur du premier attribut `DefaultTargets` découvert est utilisée. Par exemple, si ProjectA importe le projetb et le projetC (dans cet ordre) et que le projetb importe ProjectD, MSBuild commence par rechercher `DefaultTargets` spécifié sur ProjectA, puis le projetb, puis Projected et enfin le projetC.

 Le schéma d’un projet importé est identique à celui d’un projet standard. Même si MSBuild peut être en mesure de générer un projet importé, cela est peu probable, car un projet importé ne contient généralement pas d’informations sur les propriétés à définir ou l’ordre dans lequel exécuter les cibles. Le projet importé dépend du projet dans lequel il est importé pour fournir ces informations.

## <a name="wildcards"></a>Caractères génériques

 Dans le .NET Framework 4, MSBuild autorise les caractères génériques dans l’attribut de projet. Quand il existe des caractères génériques, toutes les correspondances trouvées sont triées (à des fins de reproductibilité), puis elles sont importées dans cet ordre comme si celui-ci avait été défini explicitement.

 Cela est utile si vous souhaitez offrir un point d’extensibilité pour que quelqu’un d’autre puisse importer un fichier sans avoir à ajouter explicitement le nom du fichier au fichier d’importation. À cet effet, *Microsoft. Common. targets* contient la ligne suivante en haut du fichier.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Exemple

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

- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
- [Comment : utiliser la même cible dans plusieurs fichiers projet](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)

---
title: Conditions MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbed62c13fc963af382ede113b138451303d9382
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759713"
---
# <a name="msbuild-conditions"></a>Conditions MSBuild

MSBuild prend en charge un ensemble spécifique `Condition` de conditions qui peuvent être appliquées partout où un attribut est autorisé. Le tableau suivant décrit ces conditions.

|Condition|Description|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|A la valeur `true` si `stringA` équivaut à `stringB`.<br /><br /> Par exemple :<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides.|
|'`stringA`' != '`stringB`'|A la valeur `true` si `stringA` est différent de `stringB`.<br /><br /> Par exemple :<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides.|
|\<, >, \<=, >=|Évalue les valeurs numériques des opérandes. Retourne `true` si l’évaluation relationnelle a la valeur true. Les opérandes doivent être un nombre décimal ou hexadécimal. Les nombres hexadécimaux doivent commencer par « 0x ». **Remarque :** au format XML, les caractères `<` et `>` doivent être insérés dans une séquence d’échappement. Le symbole `<` est représenté sous la forme `&lt;`. Le symbole `>` est représenté sous la forme `&gt;`.|
|Exists(« `stringA` »)|A la valeur `true` si un fichier ou un dossier du nom `stringA` existe.<br /><br /> Par exemple :<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides.|
|HasTrailingSlash (« `stringA` »)|A la valeur `true` si la chaîne spécifiée contient une barre oblique inverse finale (\\) ou une barre oblique (/).<br /><br /> Par exemple :<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides.|
|!|A la valeur `true` si l’opérande a la valeur `false`.|
|and|A la valeur `true` si les deux opérandes ont la valeur `true`.|
|ou|A la valeur `true` si l’un des opérandes au moins a la valeur `true`.|
|()|Mécanisme de regroupement qui prend la valeur `true` si les expressions qu’il contient ont la valeur `true`.|
|$if$ ( %expression% ), $else$, $endif$|Vérifie si la condition `%expression%` spécifiée correspond à la valeur de chaîne du paramètre de modèle personnalisé transmis. Si la condition `$if$` prend la valeur `true`, ses instructions sont exécutées ; dans le cas contraire, la condition `$else$` est vérifiée. Si la condition `$else$` a la valeur `true`, ses instructions sont exécutées. Dans le cas contraire, la condition `$endif$` met fin à l’évaluation de l’expression.<br /><br /> Pour des exemples d’utilisation, voir [Visual Studio projet / élément modèle de logique de paramètre](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Vous pouvez utiliser des méthodes de chaîne dans des conditions, comme le montre l’exemple suivant, dans lequel la fonction [TrimEnd()](/dotnet/api/system.string.trimend) est utilisée pour comparer uniquement la partie pertinente de la chaîne, pour différencier entre .NET Framework et .NET Core cadres cibles.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd('0123456789.'))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Voir aussi

- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [Constructions conditionnelles](../msbuild/msbuild-conditional-constructs.md)
- [Procédure pas à pas : Création d’un fichier de projet MSBuild à partir de zéro](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)

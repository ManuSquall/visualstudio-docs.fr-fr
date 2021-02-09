---
title: Conditions MSBuild | Microsoft Docs
description: Découvrez comment MSBuild prend en charge un ensemble spécifique de conditions qui peuvent être appliquées partout où un attribut de condition est autorisé.
ms.custom: SEO-VS-2020
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
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a480c539fc178e5ae672427fe32e9fd34728dc79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919165"
---
# <a name="msbuild-conditions"></a>Conditions MSBuild

MSBuild prend en charge un ensemble spécifique de conditions qui peuvent être appliquées partout où un `Condition` attribut est autorisé. Le tableau suivant décrit ces conditions.

|Condition|Description|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|A la valeur `true` si `stringA` équivaut à `stringB`.<br /><br /> Par exemple :<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides. Ce contrôle ne respecte pas la casse.|
|'`stringA`' != '`stringB`'|A la valeur `true` si `stringA` est différent de `stringB`.<br /><br /> Par exemple :<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides. Ce contrôle ne respecte pas la casse.|
|\<, >, \<=, >=|Évalue les valeurs numériques des opérandes. Retourne `true` si l’évaluation relationnelle a la valeur true. Les opérandes doivent être un nombre décimal ou hexadécimal. Les nombres hexadécimaux doivent commencer par « 0x ». **Remarque :** au format XML, les caractères `<` et `>` doivent être insérés dans une séquence d’échappement. Le symbole `<` est représenté sous la forme `&lt;`. Le symbole `>` est représenté sous la forme `&gt;`.|
|Exists(« `stringA` »)|A la valeur `true` si un fichier ou un dossier du nom `stringA` existe.<br /><br /> Par exemple :<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides.|
|HasTrailingSlash (« `stringA` »)|A la valeur `true` si la chaîne spécifiée contient une barre oblique inverse finale (\\) ou une barre oblique (/).<br /><br /> Par exemple :<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides.|
|!|A la valeur `true` si l’opérande a la valeur `false`.|
|`And`|A la valeur `true` si les deux opérandes ont la valeur `true`.|
|`Or`|A la valeur `true` si l’un des opérandes au moins a la valeur `true`.|
|()|Mécanisme de regroupement qui prend la valeur `true` si les expressions qu’il contient ont la valeur `true`.|
|$if$ ( %expression% ), $else$, $endif$|Vérifie si la condition `%expression%` spécifiée correspond à la valeur de chaîne du paramètre de modèle personnalisé transmis. Si la condition `$if$` prend la valeur `true`, ses instructions sont exécutées ; dans le cas contraire, la condition `$else$` est vérifiée. Si la condition `$else$` a la valeur `true`, ses instructions sont exécutées. Dans le cas contraire, la condition `$endif$` met fin à l’évaluation de l’expression.<br /><br /> Pour obtenir des exemples d’utilisation, consultez [logique des paramètres de modèle de projet/d’élément Visual Studio](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Vous pouvez utiliser des méthodes de chaîne dans des conditions, comme indiqué dans l’exemple suivant, dans lequel la fonction trimEnd [()](/dotnet/api/system.string.trimend) est utilisée pour comparer uniquement la partie pertinente de la chaîne, afin de faire la différence entre les .NET Framework et les frameworks cibles .net core.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

Dans les fichiers projet MSBuild, il n’existe pas de véritable type booléen. Les données booléennes sont représentées dans des propriétés qui peuvent être vides ou définies sur n’importe quelle valeur. Par conséquent, `'$(Prop)' == 'true'` signifie « si prop est » `true` , mais `'$(Prop)' != 'false'` signifie « si prop est `true` ou unset ou défini sur autre chose ».

La logique booléenne n’est évaluée que dans le contexte des conditions, donc les paramètres de propriété tels que `<Prop2>'$(Prop1)' == 'true'</Prop>` sont représentés sous forme de chaîne (après l’expansion de la variable) et ne sont pas évalués comme valeurs booléennes.  

MSBuild implémente quelques règles de traitement spéciales pour faciliter l’utilisation des propriétés de chaîne utilisées comme valeurs booléennes. Les littéraux booléens sont acceptés `Condition="true"` et `Condition="false"` fonctionnent comme prévu. MSBuild comprend également des règles spéciales pour prendre en charge l’opérateur de négation booléen. Ainsi, si `$(Prop)` a la valeur « true », se `!$(Prop)` développe à `!true` et ce compare la valeur à `false` , comme prévu.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Constructions conditionnelles](../msbuild/msbuild-conditional-constructs.md)
- [Procédure pas à pas : Créer un fichier projet MSBuild à partir de zéro](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)

---
title: Nouveautés de MSBuild 15 | Microsoft Docs
description: Consultez les fonctionnalités modifiées, mises à jour et nouvelles de MSBuild 15, disponibles pour la kit SDK .NET Core et pour la création de projets .NET Core sur Windows, macOS et Linux.
ms.custom: SEO-VS-2020
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: e0fe78e781af4f2fafa52a230036bc20b657fd8e
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848264"
---
# <a name="whats-new-in-msbuild-15"></a>Nouveautés de MSBuild 15

MSBuild fait désormais partie intégrante du [Kit de développement logiciel (SDK) .NET Core](https://www.microsoft.com/net/download/core) et peut générer des projets .NET Core sur Windows, macOS et Linux.

## <a name="changed-path"></a>Chemin d’accès modifié

 MSBuild est à présent installé dans un dossier situé sous chaque version de Visual Studio. Par exemple, *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. Vous pouvez également localiser MSBuild à l’aide du module PowerShell suivant : [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild n’est plus installé dans le Global Assembly Cache. Pour référencer MSBuild par programme, utilisez les packages NuGet. Pour plus d’informations, consultez [Mise à jour d’une application existante pour MSBuild 15.0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Propriétés modifiées

 Les propriétés MSBuild ci-après ont été mises à jour afin de correspondre au nouveau numéro de version.

- `MSBuildToolsVersion` pour cette version des outils présente la valeur 15.0. La version de l’assembly est 15.1.0.0.

- `MSBuildToolsPath` n’a plus d’emplacement fixe. Par défaut, il se trouve dans le dossier *MSBuild\15.0\Bin* relatif à l’emplacement d’installation de Visual Studio, mais l’emplacement d’installation de Visual Studio peut être modifié au moment de l’installation.

- Les valeurs `ToolsVersion` ne sont plus définies dans le Registre.

- Les propriétés `SDK35ToolsPath` et `SDK40ToolsPath` pointent vers le Kit de développement logiciel (SDK) .NET Framework, qui est fourni avec cette version de Visual Studio (par exemple, 10.0A pour les outils 4.X).

## <a name="updates"></a>Mises à jour

- L' [élément de projet](../msbuild/project-element-msbuild.md) a un nouvel `SDK` attribut. Par ailleurs, l’attribut `Xmlns` est désormais facultatif. Pour plus d’informations sur l’attribut `SDK`, voir [Guide pratique pour utiliser les kits SDK de projet MSBuild](../msbuild/how-to-use-project-sdk.md), [Packages, métapaquets et frameworks](/dotnet/core/packages) et [Ajouts au format csproj pour .NET Core](/dotnet/core/tools/csproj).
- L' [élément item](../msbuild/item-element-msbuild.md) en dehors des cibles a un nouvel `Update` attribut. En outre, la restriction sur l’attribut `Remove` a été supprimée.
- *Directory. Build. props* est un fichier défini par l’utilisateur qui fournit des personnalisations aux projets situés dans un répertoire. Ce fichier est importé automatiquement à partir de *Microsoft. Common. props* , sauf si la propriété `ImportDirectoryBuildTargets` a la valeur **false**. *Directory.Build.targets* est importé par *Microsoft.Common.targets*.
- Toutes les métadonnées dont le nom n’entre pas en conflit avec la liste d’attributs actuelle peuvent être exprimées en option sous la forme d’un attribut. Pour plus d’informations, consultez [Item, élément](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nouvelles fonctions de propriété

- `EnsureTrailingSlash` ajoute une barre oblique finale à un chemin d’accès si cette barre n’est pas déjà présente.
- `NormalizePath` combine les éléments du chemin d’accès et garantit que la chaîne de sortie présente les caractères de séparation de répertoire corrects pour le système d’exploitation actuel.
- `NormalizeDirectory` combine les éléments du chemin d’accès, vérifie l’existence d’une barre oblique finale et garantit que la chaîne de sortie présente les caractères de séparation de répertoire corrects pour le système d’exploitation actuel.
- `GetPathOfFileAbove` renvoie le chemin d’accès du fichier précédant immédiatement celui indiqué. Sur le plan fonctionnel, cette opération revient à appeler `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Voir aussi

- [MSBuild](../msbuild/msbuild.md)

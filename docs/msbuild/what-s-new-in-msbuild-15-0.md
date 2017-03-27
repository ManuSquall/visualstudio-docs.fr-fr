---
title: "Nouveautés de MSBuild 15 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
caps.latest.revision: 23
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 620d5739c450ddece13257bf7efa249ebf9c2a6a
ms.lasthandoff: 03/07/2017

---
# <a name="whats-new-in-msbuild-15"></a>Nouveautés de MSBuild 15
MSBuild fait désormais partie intégrante du [Kit de développement logiciel (SDK) .NET Core](https://www.microsoft.com/net/download/core) et peut générer des projets .NET Core sur Windows, macOS et Linux.  

## <a name="changed-path"></a>Chemin d’accès modifié
 MSBuild est à présent installé dans un dossier situé sous chaque version de Visual Studio. Par exemple, `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild`. Vous pouvez également localiser MSBuild à l’aide du module PowerShell suivant : [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild n’est plus installé dans le Global Assembly Cache. Pour référencer MSBuild par programme, utilisez les packages NuGet.

## <a name="changed-properties"></a>Propriétés modifiées  
 Les propriétés MSBuild ci-après ont été mises à jour afin de correspondre au nouveau numéro de version.  

-   `MSBuildToolsVersion` pour cette version des outils présente la valeur 15.0. La version de l’assembly est 15.1.0.0.

-   `MSBuildToolsPath` n’a plus d’emplacement fixe. Par défaut, cette propriété figure dans le dossier MSBuild\15.0\Bin relatif à l’emplacement d’installation de Visual Studio, mais cet emplacement peut être modifié pendant l’installation.

-   Les valeurs `ToolsVersion` ne sont plus définies dans le Registre.  

-   Les propriétés `SDK35ToolsPath` et `SDK40ToolsPath` pointent vers le Kit de développement logiciel (SDK) .NET Framework, qui est fourni avec cette version de Visual Studio (par exemple, 10.0A pour les outils 4.X).  

## <a name="updates"></a>Mises à jour
- [L’élément Project](../msbuild/project-element-msbuild.md) comporte un nouvel attribut `SDK`. Par ailleurs, l’attribut `Xmlns` est désormais facultatif.
- [L’élément Item](../msbuild/item-element-msbuild.md) à l’extérieur des cibles comporte un nouvel attribut `Update`. En outre, la restriction sur l’attribut `Remove` a été supprimée.
- `Directory.Build.props` est un fichier défini par l’utilisateur qui fournit des personnalisations aux projets figurant dans un répertoire. Ce fichier est automatiquement importé à partir de Microsoft.Common.targets, sauf si la propriété `ImportDirectoryBuildTargets` est définie sur **false**. `Directory.Build.targets` est importé par Microsoft.Common.targets.
- Toutes les métadonnées dont le nom n’entre pas en conflit avec la liste d’attributs actuelle peuvent être exprimées en option sous la forme d’un attribut. Pour plus d’informations, consultez l’article [Item, élément](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nouvelles fonctions de propriété

- `EnsureTrailingSlash` ajoute une barre oblique finale à un chemin d’accès si cette barre n’est pas déjà présente.
- `NormalizePath` combine les éléments du chemin d’accès et garantit que la chaîne de sortie présente les caractères de séparation de répertoire corrects pour le système d’exploitation actuel.
- `NormalizeDirectory` combine les éléments du chemin d’accès, vérifie l’existence d’une barre oblique finale et garantit que la chaîne de sortie présente les caractères de séparation de répertoire corrects pour le système d’exploitation actuel.
- `GetPathOfFileAbove` renvoie le chemin d’accès du fichier précédant immédiatement celui indiqué. Sur le plan fonctionnel, cette opération revient à appeler `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Voir aussi
[MSBuild](../msbuild/msbuild.md)


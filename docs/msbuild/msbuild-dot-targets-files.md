---
title: MSBuild .cibles Fichiers (fr) Microsoft Docs
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3faa9ca73592722a950f9914437884c33122070e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633354"
---
# <a name="msbuild-targets-files"></a>Fichiers .targets MSBuild

MSBuild comprend plusieurs fichiers *.targets* qui contiennent des éléments, des propriétés, des cibles et des tâches pour des scénarios communs. Ces fichiers sont automatiquement importés dans la plupart des fichiers de projet Visual Studio pour simplifier la maintenance et la lisibilité.

 Les projets importent généralement un ou plusieurs fichiers *.targets* pour définir leur processus de construction. Par exemple, un projet Cmd créé par Visual Studio importera *Microsoft.CSharp.targets* qui importe *Microsoft.Common.targets*. Le projet Cmd lui-même définira les éléments et les propriétés propres à ce projet, mais les règles de construction standard d’un projet Cmd sont définies dans les fichiers *.cibles* importés.

 La valeur `$(MSBuildToolsPath)` spécifie le chemin de ces fichiers *.targets* courants. Si `ToolsVersion` l’est 4.0, les fichiers sont à l’endroit suivant: * \<WindowsInstallationPath>-Microsoft.NET-Framework-v4.0.30319\\ *

> [!NOTE]
> Pour plus d’informations sur la création de vos propres cibles, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md). Pour plus d’informations `Import` sur la façon d’utiliser l’élément pour insérer un fichier de projet dans un autre fichier de projet, voir [Élément d’importation (MSBuild)](../msbuild/import-element-msbuild.md) et [Comment : Utilisez la même cible dans plusieurs fichiers de projet.](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)

## <a name="common-targets-files"></a>Fichiers .targets communs

| Fichier *.targets* | Description |
|---------------------------------| - |
| *Microsoft.Common.targets* | Définit les étapes du processus de construction standard pour les projets Visual Basic et C.<br /><br /> Importé par les fichiers *Microsoft.CSharp.targets* et *Microsoft.VisualBasic.targets*, qui incluent l’instruction suivante : `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Définit les étapes du processus de génération standard pour les projets Visual C#.<br /><br /> Importé par les fichiers projet Visual C# (*.csproj*), qui incluent l’instruction suivante: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Définit les étapes du processus de génération standard pour les projets Visual Basic.<br /><br /> Importé par visual Basic fichiers de projet (*.vbproj*), qui comprennent la déclaration suivante:`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets* est un fichier défini par l’utilisateur qui fournit des personnalisations aux projets situés dans un répertoire. Ce fichier est automatiquement importé depuis *Microsoft.Common.targets*, sauf si la propriété **ImportDirectoryBuildTargets** a la valeur **false**. Pour plus d’informations, consultez [Personnaliser votre build](customize-your-build.md).

## <a name="see-also"></a>Voir aussi

- [Import, élément (MSBuild)](../msbuild/import-element-msbuild.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)

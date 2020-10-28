---
title: LC, tâche | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche LC pour encapsuler LC.exe, qui génère un fichier. License à partir d’un fichier. licx.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70c996d5a8d1d4bf296a395bfb64ead6eba1bb01
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903583"
---
# <a name="lc-task"></a>LC (tâche)

Encapsule *LC.exe* , qui génère un fichier *.license* à partir d’un fichier *.licx* . Pour plus d’informations sur *LC.exe* , consultez [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche `LC`.

|Paramètre|Description|
|---------------|-----------------|
|`LicenseTarget`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le fichier exécutable pour lequel les fichiers *.licenses* sont générés.|
|`NoLogo`|Paramètre `Boolean` facultatif.<br /><br /> Supprime l'affichage de la bannière de démarrage Microsoft.|
|`OutputDirectory`|Paramètre `String` facultatif.<br /><br /> Spécifie le répertoire où placer les fichiers *.licenses* de sortie.|
|`OutputLicense`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le nom du fichier *. licenses* . Si vous ne spécifiez pas de nom, le nom du fichier *. licx* est utilisé et le fichier *. licenses* est placé dans le répertoire qui contient le fichier *. licx* .|
|`ReferencedAssemblies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les composants référencés à charger lors de la génération du fichier *.license* .|
|`SdkToolsPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d’accès aux outils du kit de développement logiciel (SDK), par exemple *resgen.exe* .|
|`Sources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les éléments contenant les composants sous licence à inclure dans le fichier *.licenses* . Pour plus d’informations, consultez la documentation pour l’indicateur `/complist` dans [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler).|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Exemple

L’exemple suivant utilise la tâche `LC` pour compiler des licences.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
<!-- Item declarations, etc -->

    <Target Name="CompileLicenses">
        <LC
            Sources="@(LicxFile)"
            LicenseTarget="$(TargetFileName)"
            OutputDirectory="$(IntermediateOutputPath)"
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">

            <Output
                TaskParameter="OutputLicenses"
                ItemName="CompiledLicenseFile"/>
        </LC>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)

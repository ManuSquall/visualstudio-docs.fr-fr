---
title: FileClassifier, tâche | Microsoft Docs
description: Utilisez la tâche MSBuild FileClassifier, pour classifier un ensemble de ressources sources qui seront incorporées dans un assembly.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f4a57d60c6e1dae0c42e30dce856a147fda0226
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436898"
---
# <a name="fileclassifier-task"></a>FileClassifier, tâche

La tâche <xref:Microsoft.Build.Tasks.Windows.FileClassifier> classifie un ensemble de ressources sources comme devant être incorporées dans un assembly. Si une ressource n’est pas localisable, elle est incorporée dans l’assembly principal de l’application ; autrement, elle est incorporée dans un assembly satellite.

## <a name="task-parameters"></a>Paramètres de tâche

|Paramètre|Description|
|---------------|-----------------|
|`CLREmbeddedResource`|Inutilisé.|
|`CLRResourceFiles`|Inutilisé.|
|`CLRSatelliteEmbeddedResource`|Inutilisé.|
|`Culture`|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie la culture de la build. Cette valeur peut être **null** si la build n’est pas localisable. Si la valeur est **null**, la valeur par défaut est la valeur en minuscules retournée par **CultureInfo.InvariantCulture**.|
|`MainEmbeddedFiles`|Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Spécifie les ressources non localisables incorporées dans l’assembly principal.|
|`OutputType`|Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le type de fichier dans lequel incorporer les fichiers sources spécifiés. Les valeurs valides sont **exe**, **winexe** et **library**.|
|`SatelliteEmbeddedFiles`|Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Spécifie les fichiers localisables incorporés dans l’assembly satellite pour la culture spécifiée par le paramètre **Culture**.|
|`SourceFiles`|Paramètre **ITaskItem []** obligatoire.<br /><br /> Spécifie la liste des fichiers à classifier.|

## <a name="remarks"></a>Remarques

Si le paramètre **Culture** n’est pas défini, toutes les ressources spécifiées à l’aide du paramètre **SourceFiles** sont non localisables ; sinon, elles sont localisables, sauf si elles sont associées à un attribut **Localizable** dont la valeur est **false**.

## <a name="example"></a>Exemple

L’exemple suivant classifie un fichier source unique en tant que ressource, puis l’incorpore dans un assembly satellite pour la culture Français-Canadien (fr-CA).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <ItemGroup>
    <Resource Include="Resource1.bmp" />
  </ItemGroup>
  <Target Name="FileClassifierTask">
    <FileClassifier
      SourceFiles="Resource1.bmp"
      Culture="fr-CA"
      OutputType="exe" />
  </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/wpf-msbuild-task-reference.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)

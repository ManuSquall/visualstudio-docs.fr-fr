---
title: ResourcesGenerator, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 703cd7bc3d0dd0e2229365dde39418ff32ad0a3e
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579605"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator, tâche
La tâche <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> incorpore une ou plusieurs ressources ( *.jpg*, *.ico*, *.bmp*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] au format binaire et d’autres types d’extensions) dans un fichier *.resources*.

## <a name="task-parameters"></a>Paramètres de tâche

|Paramètre|Description|
|---------------|-----------------|
|`OutputPath`|Paramètre **String** obligatoire.<br /><br /> Spécifie le chemin du répertoire de sortie. Si le chemin n’est pas absolu, il est traité comme un chemin relatif au répertoire racine du projet.|
|`OutputResourcesFile`|Paramètre de sortie **ITaskItem[]** obligatoire.<br /><br /> Spécifie le chemin et le nom du fichier *.resources* généré. Si le chemin n’est pas absolu, le fichier *.resources* est généré par rapport au répertoire racine du projet.|
|`ResourcesFiles`|Paramètre **ITaskItem[]** obligatoire.<br /><br /> Spécifie une ou plusieurs ressources à incorporer dans le fichier *.resources* généré.|

## <a name="example"></a>Exemple
 L’exemple suivant génère un fichier *.resources* avec une seule ressource *.bmp*. La ressource *.bmp* est générée dans un répertoire relatif au répertoire racine du projet.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/wpf-msbuild-task-reference.md)
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
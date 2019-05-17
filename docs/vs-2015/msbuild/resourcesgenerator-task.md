---
title: ResourcesGenerator, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa8b438727160bb5a752643f7ef9791ca5e09245
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682141"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La tâche <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> incorpore une ou plusieurs ressources (.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] au format binaire et d’autres types d’extensions) dans un fichier .resources.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`OutputPath`|Paramètre **String** obligatoire.<br /><br /> Spécifie le chemin du répertoire de sortie. Si le chemin n’est pas absolu, il est traité comme un chemin relatif au répertoire racine du projet.|  
|`OutputResourcesFile`|Paramètre de sortie **ITaskItem[]** obligatoire.<br /><br /> Spécifie le chemin et le nom du fichier .resources généré. Si le chemin n’est pas absolu, le fichier .resources est généré par rapport au répertoire racine du projet.|  
|`ResourcesFiles`|Paramètre **ITaskItem[]** obligatoire.<br /><br /> Spécifie une ou plusieurs ressources à incorporer dans le fichier .resources généré.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère un fichier .resources avec une seule ressource .bmp. La ressource .bmp est générée dans un répertoire relatif au répertoire racine du projet.  
  
```  
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
 [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/wpf-msbuild-task-reference.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Génération d’une application WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)

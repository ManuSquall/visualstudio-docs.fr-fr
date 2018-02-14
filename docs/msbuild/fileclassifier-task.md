---
title: "FileClassifier, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5f9eaf8655bba29fc0b56108c2ad62db6e3b6d48
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="fileclassifier-task"></a>FileClassifier, tâche
La tâche <xref:Microsoft.Build.Tasks.Windows.FileClassifier> classifie un ensemble de ressources sources comme devant être incorporées dans un assembly. Si une ressource n’est pas localisable, elle est incorporée dans l’assembly principal de l’application ; autrement, elle est incorporée dans un assembly satellite.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`CLREmbeddedResource`|Non utilisé.|  
|`CLRResourceFiles`|Non utilisé.|  
|`CLRSatelliteEmbeddedResource`|Non utilisé.|  
|`Culture`|Paramètre **String** facultatif.<br /><br /> Spécifie la culture de la build. Cette valeur peut être **null** si la build n’est pas localisable. Si la valeur est **null**, la valeur par défaut est la valeur en minuscules retournée par **CultureInfo.InvariantCulture**.|  
|`MainEmbeddedFiles`|Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Spécifie les ressources non localisables incorporées dans l’assembly principal.|  
|`OutputType`|Paramètre **String** obligatoire.<br /><br /> Spécifie le type de fichier dans lequel incorporer les fichiers sources spécifiés. Les valeurs valides sont **exe**, **winexe** et **library**.|  
|`SatelliteEmbeddedFiles`|Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Spécifie les fichiers localisables incorporés dans l’assembly satellite pour la culture spécifiée par le paramètre **Culture**.|  
|`SourceFiles`|Paramètre **ITaskItem[]** obligatoire.<br /><br /> Spécifie la liste des fichiers à classifier.|  
  
## <a name="remarks"></a>Notes  
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
 [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/wpf-msbuild-task-reference.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Génération d’une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
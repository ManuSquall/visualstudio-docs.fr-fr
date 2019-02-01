---
title: FileClassifier, tâche | Microsoft Docs
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
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58d81e5553fe4fd4f08bb30f5108e411b2d71c7d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803814"
---
# <a name="fileclassifier-task"></a>FileClassifier, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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
  
```  
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
 [Génération d’une application WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)

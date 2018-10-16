---
title: MergeLocalizationDirectives, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 842e36d549dab7d6e7c2f7d1da2f3e9b4db4e9d3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268201"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La tâche <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> fusionne les attributs de localisation et les commentaires d’un ou plusieurs fichiers binaires [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] en un seul fichier pour l’assembly entier.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Paramètre **ITaskItem[]** obligatoire.<br /><br /> Spécifie la liste des fichiers de directives de localisation pour des fichiers spécifiques au format binaire [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)].|  
|`OutputFile`|Paramètre de sortie **String** obligatoire.<br /><br /> Spécifie le chemin de sortie de l’assembly de directives de localisation compilé.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez ajouter des commentaires et des attributs de localisation au contenu [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]. Avec la prise en charge de la localisation [!INCLUDE[TLA#tla_wpf](../includes/tlasharptla-wpf-md.md)], vous pouvez retirer des commentaires et des attributs de localisation et les placer dans un fichier .loc distinct de l’assembly généré. Vous pouvez pour cela utiliser l’attribut **LocalizationPropertyStorage**. Pour plus d’informations sur les commentaires et attributs de localisation et sur **LocalizationPropertyStorage**, consultez [Attributs et commentaires de localisation](http://msdn.microsoft.com/library/ead2d9ac-b709-4ec1-a924-39927a29d02f).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant fusionne les commentaires de localisation de plusieurs fichiers au format binaire [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dans un seul fichier .loc.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/wpf-msbuild-task-reference.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Génération d’une application WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)




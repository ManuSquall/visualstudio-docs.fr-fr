---
title: MergeLocalizationDirectives, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5814ea188de7d3c5b7aba78ab1b239d1e9fe29e1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627218"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives, tâche
La tâche <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> fusionne les attributs de localisation et les commentaires d’un ou plusieurs fichiers binaires [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en un seul fichier pour l’assembly entier.

## <a name="task-parameters"></a>Paramètres de tâche

| Paramètre | Description |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Paramètre **ITaskItem[]** obligatoire.<br /><br /> Spécifie la liste des fichiers de directives de localisation pour des fichiers spécifiques au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. |
| `OutputFile` | Paramètre de sortie **String** obligatoire.<br /><br /> Spécifie le chemin de sortie de l’assembly de directives de localisation compilé. |

## <a name="remarks"></a>Remarques
Vous pouvez ajouter des commentaires et des attributs de localisation au contenu [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]. Avec la prise en charge de la localisation [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)], vous pouvez retirer des commentaires et des attributs de localisation, et les placer dans un fichier *.loc* distinct de l’assembly généré. Vous pouvez pour cela utiliser l’attribut **LocalizationPropertyStorage**. Pour plus d’informations sur les commentaires et attributs de localisation, et sur **LocalizationPropertyStorage**, consultez [Attributs et commentaires de localisation](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Exemple
L’exemple suivant fusionne les commentaires de localisation de plusieurs fichiers au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dans un seul fichier *.loc*.

```xml
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
- [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informations de référence sur les tâches MSBuild WPF](../msbuild/wpf-msbuild-task-reference.md)
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Informations de référence sur les tâches MSBuild](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)

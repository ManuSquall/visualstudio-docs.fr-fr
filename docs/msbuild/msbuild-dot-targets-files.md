---
title: "Fichiers .Targets MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 02/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 17
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: e212fafb9eaf7891ff75084d4d5dd8b492718049
ms.contentlocale: fr-fr
ms.lasthandoff: 06/15/2017

---
# <a name="msbuild-targets-files"></a>Fichiers .Targets MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] inclut plusieurs fichiers .targets qui contiennent des éléments, des propriétés, des cibles et des tâches pour les scénarios courants. Ces fichiers sont importés automatiquement dans la plupart des fichiers projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour en simplifier la maintenance et la lisibilité.  

 Les projets importent généralement un ou plusieurs fichiers .targets pour définir leur processus de génération. Par exemple, un projet [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] créé par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importera Microsoft.CSharp.targets, qui importe Microsoft.Common.targets. Le projet [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lui-même définit les éléments et les propriétés propres à ce projet, mais les règles de génération standard d’un projet [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sont définies dans les fichiers .targets importés.  

 La valeur `$(MSBuildToolsPath)` spécifie le chemin d’accès de ces fichiers .targets courants. Si la `ToolsVersion` est égale à 4.0, les fichiers se trouvent à l’emplacement suivant : `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  

> [!NOTE]
>  Pour plus d’informations sur la création de vos propres cibles, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md). Pour plus d’informations sur l’utilisation de l’élément `Import` pour insérer un fichier projet dans un autre fichier projet, consultez les articles [Import, élément (MSBuild)](../msbuild/import-element-msbuild.md) et [Comment : utiliser la même cible dans plusieurs fichiers projet](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  

## <a name="common-targets-files"></a>Fichiers .targets communs  

|Fichier .targets|Description|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Définit les étapes du processus de génération standard pour les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].<br /><br /> Importé par les fichiers Microsoft.CSharp.targets et Microsoft.VisualBasic.targets, qui incluent l’instruction suivante : `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Définit les étapes du processus de génération standard pour les projets Visual C#.<br /><br /> Importé par les fichiers projet Visual C# (.csproj), qui incluent l’instruction suivante : `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Définit les étapes du processus de génération standard pour les projets Visual Basic.<br /><br /> Importé par les fichiers projet Visual Basic (.vbproj), qui incluent l’instruction suivante : `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|

## <a name="directorybuildtargets"></a>Directory.Build.targets
Directory.Build.targets est un fichier défini par l’utilisateur qui fournit des personnalisations aux projets situés dans un répertoire. Ce fichier est automatiquement importé dans Microsoft.Common.targets, sauf si la propriété **ImportDirectoryBuildTargets** est définie sur **false**.

## <a name="see-also"></a>Voir aussi  
 [Import, élément (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)


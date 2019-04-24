---
title: Fichiers .Targets MSBuild | Microsoft Docs
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
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 74ac0a2c1ab50cf4c707f4fc9414fe4aa4f403b8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655060"
---
# <a name="msbuild-targets-files"></a>Fichiers .Targets MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] inclut plusieurs fichiers .targets qui contiennent des éléments, des propriétés, des cibles et des tâches pour les scénarios courants. Ces fichiers sont importés automatiquement dans la plupart des fichiers projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour en simplifier la maintenance et la lisibilité.  
  
 Les projets importent généralement un ou plusieurs fichiers .targets pour définir leur processus de génération. Par exemple, un projet [!INCLUDE[csprcs](../includes/csprcs-md.md)] créé par [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] importera Microsoft.CSharp.targets, qui importe Microsoft.Common.targets. Le projet [!INCLUDE[csprcs](../includes/csprcs-md.md)] lui-même définit les éléments et les propriétés propres à ce projet, mais les règles de génération standard d’un projet [!INCLUDE[csprcs](../includes/csprcs-md.md)] sont définies dans les fichiers .targets importés.  
  
 La valeur `$(MSBuildToolsPath)` spécifie le chemin d’accès de ces fichiers .targets courants. Si la `ToolsVersion` est égale à 4.0, les fichiers se trouvent à l’emplacement suivant : `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
>  Pour plus d’informations sur la création de vos propres cibles, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md). Pour plus d’informations sur la façon d’utiliser le `Import` élément à insérer un fichier projet dans un autre fichier de projet, consultez [Import, élément (MSBuild)](../msbuild/import-element-msbuild.md) et [Comment : Utiliser la même cible dans plusieurs fichiers projet](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>Fichiers .targets communs  
  
|Fichier .targets|Description|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Définit les étapes du processus de génération standard pour les projets [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] et [!INCLUDE[csprcs](../includes/csprcs-md.md)].<br /><br /> Importé par les fichiers Microsoft.CSharp.targets et Microsoft.VisualBasic.targets, qui incluent l’instruction suivante : `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Définit les étapes du processus de génération standard pour les projets Visual C#.<br /><br /> Importé par les fichiers projet Visual C# (.csproj), qui incluent l’instruction suivante : `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Définit les étapes du processus de génération standard pour les projets Visual Basic.<br /><br /> Importé par les fichiers projet Visual Basic (.vbproj), qui incluent l’instruction suivante : `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>Voir aussi  
 [Import, élément (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)

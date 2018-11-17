---
title: À l’aide de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dba9feb50ddab868d81eb61565c34a8c694c2a69
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768185"
---
# <a name="using-msbuild"></a>Utilisation de MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

MSBuild fournit un format XML bien défini et extensible pour la création de fichiers de projet qui décrivent entièrement les éléments de projet pour être généré, les tâches de génération et les configurations de build.  
  
 Pour obtenir un exemple de bout en bout pour un langue du système de projet basé sur MSBuild, consultez la présentation approfondie d’exemple IronPython dans le[exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md).  
  
## <a name="general-msbuild-considerations"></a>Considérations générales MSBuild  
 Fichiers de projet MSBuild, par exemple, [!INCLUDE[csprcs](../../includes/csprcs-md.md)] .csproj et [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] fichiers .vbproj, contiennent des données qui sont utilisées au moment de la génération, mais peuvent également contenir des données qui sont utilisées au moment du design. Données au moment de la build sont stockées à l’aide des primitives de MSBuild, y compris [Item, élément (MSBuild)](../../msbuild/item-element-msbuild.md) et [Property, élément (MSBuild)](../../msbuild/property-element-msbuild.md). Les données au moment du design, c'est-à-dire les données spécifiques au type de projet et les sous-types de projets connexes, sont stockées dans le format XML libre réservé pour celui-ci.  
  
 MSBuild n’a pas de prise en charge native pour les objets de configuration, mais fournit des attributs conditionnels pour spécifier les données de configuration spécifiques. Exemple :  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Pour plus d’informations sur les attributs conditionnels, consultez [constructions conditionnelles](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Extension de MSBuild pour votre Type de projet  
 Interfaces de MSBuild et API sont susceptibles de changer dans les futures versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Par conséquent, il est préférable d’utiliser les classes de framework (MPF) de package gérée, car elles offrent la protection contre les modifications.  
  
 Managed Package Framework pour les projets (MPFProj) fournit des classes d’assistance pour créer et gérer le nouveau système de projet. Vous trouverez la source des instructions de code et la compilation à [MPF pour les projets - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Les classes MPF spécifiques au projet sont les suivantes :  
  
|Classe|Implémentation|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` classe est un wrapper pour les éléments MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Visual Studio de générateurs de fichier unique. Tâches MSBuild  
 Un fichier unique générateurs sont accessibles au moment du design uniquement, mais les tâches MSBuild peuvent être utilisés au moment du design et le moment de la génération. Pour une flexibilité maximale, par conséquent, utilisez les tâches MSBuild pour transformer et générer du code. Pour plus d’informations, consultez [outils personnalisés](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Outils personnalisés](../../extensibility/internals/custom-tools.md)


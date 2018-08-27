---
title: À l’aide de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f27d3c5c7465314a7e9005972dec1349c1b9d89f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902229"
---
# <a name="using-msbuild"></a>Utilisation de MSBuild
MSBuild fournit un format XML bien défini et extensible pour la création de fichiers de projet qui décrivent entièrement les éléments de projet pour être généré, les tâches de génération et les configurations de build.  
  
## <a name="general-msbuild-considerations"></a>Considérations générales MSBuild  
 Fichiers de projet MSBuild, par exemple, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] fichiers .vbproj, contiennent des données qui sont utilisées au moment de la génération, mais peuvent également contenir des données qui sont utilisées au moment du design. Données au moment de la build sont stockées à l’aide des primitives de MSBuild, y compris [Item, élément (MSBuild)](../../msbuild/item-element-msbuild.md) et [Property, élément (MSBuild)](../../msbuild/property-element-msbuild.md). Les données au moment du design, c'est-à-dire les données spécifiques au type de projet et les sous-types de projets connexes, sont stockées dans le format XML libre réservé pour celui-ci.  
  
 MSBuild n’a pas de prise en charge native pour les objets de configuration, mais fournit des attributs conditionnels pour spécifier les données de configuration spécifiques. Exemple :  
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Pour plus d’informations sur les attributs conditionnels, consultez [constructions conditionnelles](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Extension de MSBuild pour votre Type de projet  
 Interfaces de MSBuild et API sont susceptibles de changer dans les futures versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Par conséquent, il est préférable d’utiliser les classes de framework (MPF) de package gérée, car elles offrent la protection contre les modifications.  
  
 Managed Package Framework pour les projets (MPFProj) fournit des classes d’assistance pour créer et gérer le nouveau système de projet. Vous trouverez la source des instructions de code et la compilation à [MPF pour les projets - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).  
  
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
 [MSBuild](../../msbuild/msbuild.md)   
 [Outils personnalisés](../../extensibility/internals/custom-tools.md)
---
title: "&#192; l’aide de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, compiler avec MSBuild"
  - "MSBuild, d’extensibilité"
  - "packages, compiler avec MSBuild"
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# &#192; l’aide de MSBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

MSBuild fournit un format XML bien défini et extensible pour la création de fichiers de projet qui décrivent complètement les éléments de projet pour être généré, tâches de génération et les configurations de build.  
  
 Pour un exemple de bout en bout pour un langue du système de projet basé sur MSBuild, consultez la présentation approfondie du exemple IronPython dans le[Exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md).  
  
## Considérations générales MSBuild  
 Fichiers de projet MSBuild, par exemple, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] fichiers .vbproj, contiennent des données qui sont utilisées au moment de la génération, mais peuvent également contenir des données qui sont utilisées au moment du design. Les données au moment de la build sont stockées à l’aide de MSBuild primitives, notamment [Item Element \(MSBuild\)](../../msbuild/item-element-msbuild.md) et [Property Element \(MSBuild\)](../../msbuild/property-element-msbuild.md). Les données au moment du design, c'est\-à\-dire les données spécifiques au type de projet et les sous\-types de projets connexes, sont stockées au format XML libre réservé pour lui.  
  
 MSBuild n’a pas de prise en charge native pour les objets de configuration, mais fournit des attributs conditionnels pour spécifier les données de configuration spécifiques. Exemple :  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Pour plus d’informations sur les attributs conditionnels, consultez [Conditional Constructs](../../msbuild/msbuild-conditional-constructs.md).  
  
### Extension de MSBuild pour votre Type de projet  
 Interfaces de MSBuild et les API est susceptibles de changer dans les futures versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Par conséquent, il est préférable d’utiliser les classes du framework \(MPF\) package managé, car ils offrent la protection contre les modifications.  
  
 Managed Package Framework pour les projets \(MPFProj\) fournit des classes d’assistance pour créer et gérer le nouveau système de projet. Vous trouverez la source des instructions de code et la compilation au [MPF de projets de Visual Studio 2013 \-](http://mpfproj12.codeplex.com/).  
  
 Les classes MPF spécifiques au projet sont les suivantes :  
  
|Classe|Implémentation|  
|------------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` classe est un wrapper pour les éléments MSBuild.  
  
#### Vs générateurs de fichier unique. Tâches MSBuild  
 Un fichier unique générateurs sont accessibles au moment du design uniquement, mais les tâches MSBuild peuvent être utilisés au moment du design et au moment de la build. Pour une flexibilité maximale, par conséquent, utilisez les tâches MSBuild pour transformer et générer le code. Pour plus d'informations, consultez [Outils personnalisés](../../extensibility/internals/custom-tools.md).  
  
## Voir aussi  
 [MSBuild Reference](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/fr-fr/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Outils personnalisés](../../extensibility/internals/custom-tools.md)
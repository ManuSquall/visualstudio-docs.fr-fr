---
title: "Param&#232;tres rempla&#231;ables | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "paramètres remplaçables (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, paramètres remplaçables"
  - "développement SharePoint dans Visual Studio, jetons"
  - "jetons (développement SharePoint dans Visual Studio)"
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Param&#232;tres rempla&#231;ables
  Les paramètres remplaçables, ou *jetons*, peuvent être utilisés à l'intérieur des fichiers projet pour fournir des valeurs aux éléments de solution SharePoint dont les valeurs réelles ne sont pas connues au moment du design.  Ils sont similaires en fonction des jetons du modèle standard [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Pour plus d'informations, consultez [Paramètres de modèle](../ide/template-parameters.md).  
  
## Format d'un jeton  
 Les jetons commencent et se terminent par le signe dollar \($\).  Les jetons employés sont remplacés par les valeurs réelles dès lors que le projet est empaqueté dans un fichier de package de solution \(.wsp\) SharePoint au moment du déploiement.  Par exemple, le jeton **$SharePoint.Package.Name$** peut prendre la valeur de chaîne « Test du package SharePoint ».  
  
## Règles applicables aux jetons  
 Les jetons doivent respecter les règles suivantes :  
  
-   Les jetons peuvent être spécifiés à un endroit quelconque sur une ligne.  
  
-   Les jetons ne peuvent pas s'étendre sur plusieurs lignes.  
  
-   Le même jeton peut être spécifié plusieurs fois sur la même ligne et au sein du même fichier.  
  
-   Une même ligne peut contenir plusieurs jetons différents.  
  
 Les jetons non conformes à ces règles sont ignorés et ne donnent lieu à aucun avertissement ou erreur.  
  
 Le remplacement des jetons par des valeurs de chaîne s'effectue immédiatement après la transformation du manifeste, autorisant ainsi les modèles de manifeste modifiés par un utilisateur à utiliser des jetons.  
  
### Résolution des noms de jeton  
 Dans la plupart des cas, un jeton prend une valeur spécifique indépendamment de son emplacement.  En revanche, si le jeton est lié à un package ou une fonctionnalité, sa valeur dépend de son emplacement.  Par exemple, si une fonctionnalité figure dans le Package A, le jeton `$SharePoint.Package.Name$` prend la valeur « Package A ». Si la même fonctionnalité figure dans le Package B,  `$SharePoint.Package.Name$` prend la valeur « Package B ».  
  
## Liste des jetons  
 Le tableau suivant répertorie l'ensemble des jetons disponibles.  
  
|Nom|Description|  
|---------|-----------------|  
|$SharePoint.Project.FileName$|Nom du fichier projet contenant, par exemple « NouvProj.csproj ».|  
|$SharePoint.Project.FileNameWithoutExtension$|Nom du fichier projet contenant sans l'extension de nom de fichier.  Par exemple, « NouvProj ».|  
|$SharePoint.Project.AssemblyFullName$|Nom complet \(nom fort\) de l'assembly de sortie du projet contenant.|  
|$SharePoint.Project.AssemblyFileName$|Nom de l'assembly de sortie du projet contenant.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Nom de l'assembly de sortie du projet contenant sans l'extension de nom de fichier.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Jeton de clé publique de l'assembly de sortie du projet contenant, converti en chaîne. \(16 caractères au format hexadécimal « x2 ».\)|  
|$SharePoint.Package.Name$|Nom du package contenant.|  
|$SharePoint.Package.FileName$|Nom du fichier de définition du package contenant.|  
|$SharePoint.Package.FileNameWithoutExtension$|Nom \(sans extension\) du fichier de définition du package contenant.|  
|$SharePoint.Package.Id$|ID SharePoint du package contenant.  Si une fonctionnalité est utilisée dans plusieurs packages, cette valeur changera.|  
|$SharePoint.Feature.FileName$|Nom du fichier de définition de la fonctionnalité contenante, par exemple Fonctionnalite1.feature.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Nom du fichier de définition de la fonctionnalité, sans l'extension du nom de fichier.|  
|$SharePoint.Feature.DeploymentPath$|Nom du dossier contenant la fonctionnalité dans le package.  Ce jeton équivaut à la propriété « Chemin d'accès du déploiement » dans le Concepteur de fonctionnalités.  Une valeur d'exemple peut être « Projet1\_Fonctionnalite1 ».|  
|$SharePoint.Feature.Id$|ID SharePoint de la fonctionnalité contenante.  Ce jeton, comme tous les jetons de niveau fonctionnalité, peut être utilisé uniquement par les fichiers inclus dans un package via une fonctionnalité et non ajouté directement à un package en dehors d'une fonctionnalité.|  
|$SharePoint.ProjectItem.Name$|Nom de l'élément de projet \(et non son nom de fichier\), tel qui est obtenu de **ISharePointProjectItem.Name**.|  
|$SharePoint.Type.\<GUID\>.AssemblyQualifiedName$|Le nom qualifié de l'assembly du type correspondant à [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] du jeton.  Le [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] est en minuscules et son format correspond au format Guid.ToString\("D"\) \(autrement dit, xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx\).|  
|$SharePoint.Type.\<GUID\>.FullName$|Nom complet du type correspondant au GUID dans le jeton.  Le GUID est en minuscules et son format correspond au format Guid.ToString\("D"\) \(autrement dit, xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx\).|  
  
## Ajout d'extensions à la liste des extensions de fichiers de remplacement de jeton  
 Bien que les jetons puissent, en théorie, être utilisés par tout fichier appartenant à un élément de projet SharePoint inclus dans le package, par défaut, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] recherche les jetons exclusivement dans les fichiers de package, les fichiers de manifeste et les fichiers portant les extensions suivantes :  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Webpart  
  
-   DWP  
  
 Ces extensions sont définies par l'élément `<TokenReplacementFileExtensions>` dans le fichier Microsoft.VisualStudio.SharePoint.targets, situé dans le dossier …\\\<program files\>\\MSBuild\\Microsoft\\VisualStudio\\v11.0\\SharePointTools  
  
 Il est possible, toutefois, d'ajouter des extensions de fichier supplémentaires à la liste.  Pour ce faire, ajoutez un élément `<TokenReplacementFileExtensions>` à tout PropertyGroup dans le fichier projet SharePoint défini avant la balise \<Import\> du fichier de cibles SharePoint.  
  
> [!NOTE]  
>  Étant donné que le remplacement de jetons s'effectue après la compilation d'un projet, vous ne devez pas ajouter d'extensions de fichier pour les types de fichiers compilés, tels que .cs, .vb ou .resx.  Les jetons sont remplacés uniquement dans les fichiers qui ne sont pas compilés.  
  
 Par exemple, pour ajouter les extensions de nom de fichier « .myextension » et « .yourextension » à la liste des extensions de noms de fichier de remplacement de jeton, insérez ce qui suit dans un fichier .csproj :  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Il est possible également d'ajouter directement l'extension au fichier .targets.  Cependant, cela a pour effet de modifier la liste des extensions pour tous les projets SharePoint empaquetés sur le système local, et non pas uniquement votre propre liste.  Cela peut être pratique si vous êtes le seul développeur du système ou si la plupart de vos projets nécessitent ce changement.  Toutefois, étant donné que cette approche est spécifique au système, elle n'est pas réellement transposable. Par conséquent, il est préférable d'ajouter les extensions au fichier projet.  
  
## Voir aussi  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  
---
title: "Outils personnalis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, des outils personnalisés"
  - "outils (Visual Studio), personnalisés"
  - "outils personnalisés"
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Outils personnalis&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

*Les outils personnalisés* vous permettent d'associer un outil avec un élément dans un projet et exécuter cet outil chaque fois que le fichier est enregistré.  Certains outils personnalisés, parfois appelés *générateurs de fichier unique*, sont souvent utilisés pour implémenter les traducteurs qui génèrent du code des données et vice versa.  Par exemple, les générateurs de fichier unique créent [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et le code source de[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] hors de les fichiers .settings et .resx.  Code source généré fournit un accès fortement typé aux données dans les fichiers .settings et .resx.  les types de projet de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et de[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] prennent en charge les outils personnalisés ; les types de projet de [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] ne stocke pas.  Vos propres types de projets peuvent également prendre en charge les outils personnalisés.  
  
 Les outils personnalisés sont des composants inscrits qui implémentent l'interface d' `IVsSingleFileGenerator` .  
  
 Les outils personnalisés sont associés à un objet d'interface d' `ProjectItem` , et sont comme les concepteurs et les éditeurs.  Un outil personnalisé prend le fichier représenté par `ProjectItem` comme entrée et écrit un fichier dont le nom de fichier est fourni par la méthode d' `DefaultExtension` .  
  
## Dans cette section  
 [L'implémentation de générateurs de fichier unique](../../extensibility/internals/implementing-single-file-generators.md)  
 Décrit comment utiliser l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> pour implémenter un outil personnalisé.  
  
 [Détermination de l’espace de noms par défaut d’un projet](../../misc/determining-the-default-namespace-of-a-project.md)  
 Décrit comment déterminer l'espace de noms approprié en fonction de le langage utilisé.  
  
 [Enregistrement de générateurs de fichier unique](../../extensibility/internals/registering-single-file-generators.md)  
 fournit des descriptions pour toutes les entrées du Registre pour un outil personnalisé.  
  
 [Exposer des Types pour les concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explique comment les systèmes de projet prennent en charge les concepteurs visuels aux classes et aux types générés par accès au sein de les fichiers exécutables portables temporaires \(PE\).  
  
 [Conserver la propriété d'un élément de projet](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Indique comment rendre une propriété d'élément de projet, telle que l'auteur d'un fichier source, dans le fichier projet.  
  
## Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Fournit des détails concernant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, qui convertit un fichier d'entrée unique dans un fichier de sortie unique qui peut être compilé ou ajouté à un projet.  
  
 <xref:EnvDTE.ProjectItem>  
 Explique l'interface d' `ProjectItem` , qui représente un élément d'un projet.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Fournit des détails sur la méthode d' `DefaultExtension` , qui récupère l'extension de nom de fichier fourni sur le nom du fichier de sortie.  
  
## Rubriques connexes  
 [Étendre des projets](../../extensibility/extending-projects.md)  
 décrit comment utiliser des projets et des solutions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] d'organiser des fichiers et des fichiers de ressources de code, et comment implémenter le contrôle de code source.
---
title: "Structure VSPackage (VSPackage du contr&#244;le de code Source) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, structure"
  - "packages de contrôle de source, vue d’ensemble du package VS"
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Structure VSPackage (VSPackage du contr&#244;le de code Source)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le Kit de développement logiciel Source contrôle Package fournit des directives pour la création d’un VSPackage qui autorisent un implémenteur de contrôle source pour intégrer sa fonctionnalité de contrôle de code source avec le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement. Un VSPackage est un composant COM qui est généralement chargé à la demande par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré \(IDE\) basée sur les services qui sont publiés par le package dans ses entrées de Registre. Chaque VSPackage doit implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Un VSPackage consomme généralement les services offerts par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE et proffers certains services qui lui sont propres.  
  
 Un VSPackage déclare ses éléments de menu et établit un état d’élément par défaut via le fichier .vsct. Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE affiche les éléments de menu dans cet état jusqu'à ce que le VSPackage est chargé. Par la suite, du VSPackage mise en oeuvre de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode est appelée pour activer ou désactiver des éléments de menu.  
  
## Caractéristiques de Package de contrôle de code source  
 Un contrôle de code source VSPackage est profondément intégré à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 La sémantique VSPackage est les suivantes :  
  
-   Interface à implémenter parce qu’il était un VSPackage \(le `IVsPackage` interface\)  
  
-   Implémentation de la commande de l’interface utilisateur \(fichier .vsct et l’implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface\)  
  
-   L’inscription du package VS avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Le contrôle de code source VSPackage doit communiquer avec les autres [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entités :  
  
-   Projets  
  
-   Éditeurs  
  
-   Solutions  
  
-   Windows  
  
-   La table de document en cours d’exécution  
  
### Services de l’environnement Visual Studio qui peuvent être consommés.  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Service de SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### Interfaces VSIP implémentée et appelée  
 Un package de contrôle de code source est un VSPackage, et par conséquent, il peut interagir directement avec les autres packages VS qui sont enregistrés avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Afin d’offrir la gamme complète des fonctionnalités de contrôle de code source, un contrôle de code source VSPackage peut prendre en charge les interfaces fournies par l’interpréteur de commandes ou des projets.  
  
 Chaque projet dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> à être reconnu comme un projet dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Toutefois, cette interface n’est pas spécialisée suffisante pour le contrôle de code source. Les projets qui sont censés être sous la source de contrôle implémentent la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Cette interface est utilisée par le contrôle de code source VSPackage pour interroger un projet pour son contenu et lui fournir des glyphes et des informations de liaison \(les informations nécessaires pour établir une connexion entre l’emplacement du serveur et l’emplacement du disque d’un projet qui est sous contrôle de code source\).  
  
 Le contrôle de code source VSPackage implémente le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, qui permet à son tour des projets pour s’inscrire pour le contrôle de code source et récupérer les glyphes de leur état.  
  
 Pour obtenir une liste complète des interfaces dans un contrôle de code source VSPackage doit prendre en compte, consultez la page [Les interfaces et les Services connexes](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## Voir aussi  
 [Éléments de conception.](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Les interfaces et les Services connexes](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
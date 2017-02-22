---
title: "L&#39;impl&#233;mentation de g&#233;n&#233;rateurs de fichier unique | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "l'implémentation des outils personnalisés"
  - "projets d'extensibilité Visual Studio SDK,"
  - "projets (Visual Studio SDK), gérée des outils personnalisés"
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# L&#39;impl&#233;mentation de g&#233;n&#233;rateurs de fichier unique
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un outil personnalisé \(parfois appelée génération d'un générateur de fichier unique \)peut être utilisé pour étendre [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] et les systèmes de projet csprcs dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  un outil personnalisé est un composant COM qui implémente l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  Cette interface, un outil personnalisé fait un fichier d'entrée unique dans un fichier de sortie unique.  Le résultat de la transformation peut être code source, ou toute autre sortie qui est utile.  Deux exemples de fichiers de code outil\-générés personnalisés sont le code généré en réponse à des modifications d'un concepteur visuel et les fichiers générés à l'aide de Web Services Description \(WSDL\) langage\).  
  
 Lorsqu'un outil personnalisé est chargé, ou le fichier d'entrée est enregistré, le système de projet appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> , et passe une référence à une interface de rappel d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> , par laquelle l'outil puisse stocker sa progression à l'utilisateur.  
  
 Le fichier de sortie que l'outil personnalisé génère l'erreur est ajouté au projet avec une dépendance sur le fichier d'entrée.  Le système de projet détermine automatiquement le nom du fichier de sortie, en fonction de la chaîne retournée par l'implémentation personnalisée de l'outil d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 un outil personnalisé doit implémenter l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  Éventuellement, des outils personnalisés prennent en charge l'interface d' <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> pour récupérer des informations sur les sources autres que le fichier d'entrée.  Dans tous les cas, avant de pouvoir utiliser un outil personnalisé, vous devez l'inscrire dans le système ou le Registre locaux de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Pour plus d'informations sur l'inscription des outils personnalisés, consultez [Enregistrement de générateurs de fichier unique](../../extensibility/internals/registering-single-file-generators.md).  
  
## Voir aussi  
 [Détermination de l’espace de noms par défaut d’un projet](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Exposer des Types pour les concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)
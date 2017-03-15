---
title: "Utilisation de polices et couleurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "polices, contrôler dans l'IDE"
  - "IDE, contrôler la couleur du texte et des polices"
  - "Page de propriétés de polices et couleurs"
  - "contrôle de la police et la couleur (Visual Studio SDK)"
  - "texte, IDE"
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Utilisation de polices et couleurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit la prise en charge d'utiliser des polices et les couleurs du texte.  
  
## Dans cette section  
 [Vue d'ensemble de la couleur et de police](../extensibility/font-and-color-overview.md)  
 Décrit la police et les paramètres de couleur de texte dans l'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Introduit également les concepts des catégories et des éléments d'affichage, et explique comment les VSPackages et l'éditeur principal utilisent des attributs de texte.  
  
 [Mise en route de la police et les informations de couleur de colorisation de texte](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Fournit des règles sur l'implémentation de la colorisation de texte dans les VSPackages qui gèrent **Catégories** autre qu' **Éditeur de texte**.  
  
 [L'accès à stockée paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md)  
 Explique comment la police actuelle et des paramètres de couleurs peuvent être enregistrés, récupérés, et appliqués.  
  
 [L'implémentation des catégories personnalisées et afficher les éléments](../extensibility/implementing-custom-categories-and-display-items.md)  
 Décrit les étapes de base par lesquelles une fenêtre peut la créer et utilise son propre d' **Éléments affichés** et de **Catégories** pour prendre en charge l'affichage de texte.  
  
 Cette approche requiert un VSPackage pour implémenter l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> et les interfaces connexes.  
  
 [Comment : accéder aux polices intégrées et jeu de couleurs](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Explique comment définir et inscrire une catégorie à l'aide de les polices prédéfinies et les couleurs, et initialise l'utilisation de polices fournies par le système et de couleurs.  
  
## Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 fournit une instance d' `IVsFontAndColorDefaults` ou de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> qui correspond à un point particulier répertorié dans la liste d' **Afficher les paramètres de** dans la page de **Polices et couleurs** de la boîte de dialogue d' **Options** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Permet à un VSPackage pour prendre en charge la page de l'IDE **Polices et couleurs** en définissant les polices par défaut et de couleurs pour une fenêtre ou l'interface utilisateur.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Fournit un mécanisme par lequel un VSPackage qui contribue la police et prise en charge des couleurs peut spécifier un groupe d'éléments d'affichage \- une superbe\-catégorie qui représente l'union de deux catégories ou plus.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Permet à un VSPackage pour récupérer la police et aux données, ou le sauvegarde au Registre.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Informe VSPackages qui utilisent la police et des informations sur la couleur relatives aux modifications de police et les paramètres de couleurs.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Fournit des outils pour utiliser les données d'entrée et de sortie qui est utilisée par les méthodes de mécanisme de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**Police et couleurs** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Contrôle la mise en cache de police et les paramètres de couleurs.  
  
## Rubriques connexes  
 [Développement d'un Service de langage](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explique comment VSPackages peut utiliser des services linguistiques de personnaliser l'éditeur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)  
 Aperçoit de comprendre comment l'éditeur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilise des services de langage pour implémenter la coloration de syntaxe.  
  
 [Extension des autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment utiliser les services de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour créer des éléments d'interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
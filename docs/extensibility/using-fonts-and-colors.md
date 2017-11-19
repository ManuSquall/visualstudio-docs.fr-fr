---
title: "À l’aide des polices et couleurs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ce64c7cac36319d1e55efb0ddf2216dc218805c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="using-fonts-and-colors"></a>À l’aide des polices et couleurs
Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit la prise en charge pour l’utilisation des polices et couleurs pour afficher le texte.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de la couleur et de police](../extensibility/font-and-color-overview.md)  
 Décrit les paramètres de police et la couleur du texte dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Également présente les concepts de catégories et les éléments d’affichage et décrit comment les VSPackages et l’éditeur principal utilisent les attributs de texte.  
  
 [Mise en route de la police et les informations de couleur de colorisation de texte](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Fournit des instructions pour l’implémentation de colorisation de texte dans les VSPackages gérer **catégories** autre que **éditeur de texte**.  
  
 [L’accès à la police stockée et les paramètres de couleur](../extensibility/accessing-stored-font-and-color-settings.md)  
 Explique comment actuel de police et de couleur paramètres peuvent être stockées, extraites et appliquées.  
  
 [Implémentation des catégories personnalisées et des éléments d’affichage](../extensibility/implementing-custom-categories-and-display-items.md)  
 Décrit les étapes de base par lequel une fenêtre peut créer et utiliser son propre de **afficher les éléments** et **catégories** pour prendre en charge d’affichage du texte.  
  
 Cette approche nécessite un VSPackage implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface et des interfaces associées.  
  
 [Comment : accéder aux polices intégrées et jeu de couleurs](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Explique comment définir et enregistrer une catégorie à l’aide de couleurs et polices intégrées et lancer l’utilisation de couleurs et polices fournies par le système.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Fournit une instance de la `IVsFontAndColorDefaults` ou le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interface qui correspond à un élément particulier répertorié dans le **afficher les paramètres de** liste dans le **polices et couleurs** page de la **Options** boîte de dialogue.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Permet à un VSPackage prendre en charge de l’IDE **polices et couleurs** page en définissant des polices par défaut et les couleurs d’une fenêtre ou un composant d’interface utilisateur.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Fournit un mécanisme par lequel un VSPackage qui fournit la prise en charge de police et couleur peut spécifier un groupe d’élément d’affichage - super une catégorie qui représente l’union de deux ou plusieurs catégories.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Permet à un VSPackage récupérer les données de police et la couleur, ou l’enregistrer dans le Registre.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Notifie les VSPackages qui utilisent la police et la couleur des informations sur les modifications dans les paramètres de police et couleur.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Fournit des outils permettant de travailler avec les données d’entrée et de sortie qui sont utilisées par les méthodes de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **police et couleur** mécanisme.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Contrôle la mise en cache des paramètres de police et couleur.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Développement d’un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explique comment les VSPackages peuvent utiliser les services de langage pour personnaliser le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur.  
  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)  
 Explique comment la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur utilise les services de langage pour implémenter la coloration de syntaxe.  
  
 [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] services pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
---
title: Utilisation de polices et couleurs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32bbfb4957dbeb351055ab3f73c7a29087349636
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338042"
---
# <a name="using-fonts-and-colors"></a>Utilisation des polices et couleurs
Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit la prise en charge pour l’utilisation des polices et couleurs pour afficher le texte.

## <a name="in-this-section"></a>Dans cette section
- [Vue d’ensemble de la couleur et de police](../extensibility/font-and-color-overview.md) traite les paramètres de police et la couleur du texte dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Également présente les concepts de catégories et les éléments d’affichage et décrit comment les VSPackages et l’éditeur principal utilisent les attributs de texte.

- [L’obtention de la police et les informations de couleur pour la colorisation de texte](../extensibility/getting-font-and-color-information-for-text-colorization.md) fournit des instructions pour l’implémentation de la colorisation de texte dans les VSPackages gérer **catégories** autre que **éditeur de texte**.

- [L’accès à stockées paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md) Explains comment les paramètres de police et la couleur actuelles peuvent être stockés, extraction et l’application.

- [Implémentation des catégories personnalisées et afficher les éléments](../extensibility/implementing-custom-categories-and-display-items.md) décrit les étapes de base par lequel une fenêtre peut créer et utiliser sa propre de **afficher les éléments** et **catégories** pour prendre en charge d’affichage de texte.

 Cette approche nécessite un VSPackage implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface et des interfaces associées.

- [Guide pratique pour Le jeu de couleurs et polices intégrées d’accès](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md) explique comment définir et enregistrer une catégorie à l’aide de couleurs et polices intégrées et lancer l’utilisation de couleurs et polices fournies par le système.

## <a name="reference"></a>Référence
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> Fournit une instance de la `IVsFontAndColorDefaults` ou le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interface qui correspond à un élément particulier répertorié dans le **afficher les paramètres de** liste dans le **polices et couleurs** page de la **Options** boîte de dialogue.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Permet à un VSPackage prendre en charge de l’IDE **polices et couleurs** page en définissant des polices par défaut et les couleurs d’une fenêtre ou d’un composant d’interface utilisateur.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Fournit un mécanisme par lequel un VSPackage qui fournit la prise en charge de police et de couleur peut spécifier un groupe d’élément d’affichage - une super-catégorie qui représente l’union de deux ou plusieurs catégories.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Permet à un VSPackage récupérer les données de police et couleur, ou l’enregistrer dans le Registre.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Informe les VSPackages qui sont à l’aide de police et la couleur des informations sur les modifications dans les paramètres de police et couleur.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities> Fournit des outils pour travailler avec les données d’entrée et de sortie qui sont utilisées par les méthodes de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **police et couleur** mécanisme.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Contrôle la mise en cache des paramètres de police et couleur.

## <a name="related-sections"></a>Rubriques connexes
- [Développement d’un Service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md) explique comment les VSPackages peuvent utiliser des services de langage pour personnaliser le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur.

- [Couleurs de syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md) Descries comment la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur utilise les services de langage pour implémenter la coloration syntaxique.

- [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md) explique comment utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] services pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
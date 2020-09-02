---
title: Utilisation des polices et des couleurs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177224"
---
# <a name="using-fonts-and-colors"></a>Utilisation des polices et couleurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] fournit la prise en charge de l’utilisation des polices et des couleurs pour afficher le texte.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Présentation de la couleur et de la police](../extensibility/font-and-color-overview.md)  
 Décrit les paramètres de police et de couleur du texte dans l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement de développement intégré (IDE). Présente également les concepts des catégories et des éléments d’affichage, et décrit comment les VSPackages et l’éditeur de base utilisent des attributs de texte.  
  
 [Obtention des informations sur la couleur et la police pour la colorisation du texte](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Fournit des instructions pour l’implémentation de la colorisation de texte dans des VSPackages qui gèrent des **catégories** autres que l' **éditeur de texte**.  
  
 [Accès aux paramètres de police et de couleur stockés](../extensibility/accessing-stored-font-and-color-settings.md)  
 Explique comment les paramètres actuels de la police et de la couleur peuvent être stockés, récupérés et appliqués.  
  
 [Implémentation de catégories personnalisées et d’éléments d’affichage](../extensibility/implementing-custom-categories-and-display-items.md)  
 Décrit les étapes de base permettant à une fenêtre de créer et d’utiliser ses propres éléments et **catégories** d' **affichage** pour prendre en charge l’affichage de texte.  
  
 Cette approche nécessite un VSPackage pour implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface et les interfaces associées.  
  
 [Guide pratique pour accéder aux polices intégrées et au modèle de couleurs](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Explique comment définir et inscrire une catégorie à l’aide de polices et de couleurs intégrées, et comment initier l’utilisation de polices et de couleurs fournies par le système.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Fournit une instance de l' `IVsFontAndColorDefaults` interface ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> qui correspond à un élément particulier répertorié dans la liste **afficher les paramètres de** dans la page **polices et couleurs** de la boîte de dialogue **options** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Permet à un VSPackage de prendre en charge la page **polices et couleurs** IDE en définissant les polices et les couleurs par défaut pour une fenêtre ou un composant d’interface utilisateur.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Fournit un mécanisme par lequel un VSPackage qui fournit la prise en charge des polices et des couleurs peut spécifier un groupe d’éléments d’affichage, une super catégorie qui représente l’Union de deux ou plusieurs catégories.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Permet à un VSPackage de récupérer des données de police et de couleur, ou de les enregistrer dans le registre.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Notifie les VSPackages qui utilisent les informations de police et de couleur sur les modifications des paramètres de police et de couleur.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Fournit des outils pour l’utilisation des données d’entrée et de sortie qui sont utilisées par les méthodes du mécanisme de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **police et de couleur** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Contrôle la mise en cache des paramètres de couleurs et de police.  
  
## <a name="related-sections"></a>Sections connexes  
 [Développement d’un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explique comment les VSPackages peuvent utiliser les services de langage pour personnaliser l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur.  
  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries comment l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur utilise les services de langage pour implémenter la coloration de la syntaxe.  
  
 [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment utiliser les services de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

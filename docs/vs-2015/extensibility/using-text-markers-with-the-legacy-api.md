---
title: À l’aide de marqueurs de texte avec l’API héritée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 03b68c0fbaf92ff2c768c36ccdbea1988c99a973
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430113"
---
# <a name="using-text-markers-with-the-legacy-api"></a>À l’aide de marqueurs de texte avec l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un marqueur de texte est une plage flottante de texte dans une mémoire tampon qui peut affecter l’affichage et le comportement d’une zone de texte. Marqueurs incluent des points d’arrêt, les signets, les soulignements ondulés et les zones en lecture seule. Marqueurs de texte sont fondamentalement différents à partir de la coloration syntaxique. Coloration de la syntaxe est un moyen rapide de communiquer la syntaxe du langage qui est associée à une zone de texte. Coloration de la syntaxe est généralement demandée lorsque Windows redessine l’écran, la vitesse est importante. La coloration syntaxique modifie uniquement la couleur du texte. Marqueurs de texte peuvent modifier de nombreuses autres propriétés de texte. Marqueurs de texte peuvent « flotter » et appliquer un comportement particulier et la couleur.  
  
 En raison de la surcharge de performances associée aux marqueurs de texte, ne créez pas plusieurs marqueurs pour vos tampons de texte. Chaque marqueur est mis à jour chaque fois qu’un utilisateur modifie le contenu de la mémoire tampon.  
  
> [!NOTE]
> Les utilisateurs peuvent modifier la couleur d’un type de marqueur visible mais pas sa forme et son style. Pour plus d’informations, consultez [polices et couleurs, environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour ajouter des marqueurs de texte standard](../extensibility/how-to-add-standard-text-markers.md)|Décrit comment ajouter un type de marqueur de texte standard fourni par le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur principal pour un affichage de texte.|  
|[Guide pratique pour implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)|Décrit comment implémenter une instance de la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] marqueur qui sert à indiquer les erreurs à l’aide des soulignements ondulés rouges.|  
|[Guide pratique pour créer des marqueurs de texte personnalisés](../extensibility/how-to-create-custom-text-markers.md)|Décrit comment créer et ajouter un type de marqueur de texte personnalisé à une vue de texte.|  
|[Guide pratique pour utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)|Explique comment ajouter des marqueurs de texte.|  
|[Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)|Décrit les fonctionnalités de l’éditeur principal et fournit des détails sur la personnalisation de l’éditeur principal.|  
|[Fonctionnalités de l’éditeur](http://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Décrit les fonctionnalités disponibles dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur principal.|  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Fournit un mécanisme uniforme pour obtenir des informations sur un type de marqueur de texte spécifique, si prédéfini par l’éditeur ou inscrit par un VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Permet d’accéder à et ajuste la position d’un marqueur de texte dans une mémoire tampon de texte à l’aide de coordonnées à deux dimensions.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Fournit des méthodes pour la gestion des marqueurs de texte.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Fournit des rappels à la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE et d’autres processus qui sont utilisés pour ajuster un marqueur de texte.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Étend les fonctionnalités qui sont disponible via le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface en fournissant des rappels supplémentaires.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Étend les fonctionnalités qui sont disponible via le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface en fournissant des rappels supplémentaires.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Permet à un type de marqueur déterminer si autres types de marqueur d'partagent le même jeu de couleurs.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Fournit le contexte pour les marqueurs de texte dans l’éditeur principal. Pour chaque type de marqueur de texte qui se trouve dans l’éditeur principal, l’IDE crée un distinct <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> objet.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Un gestionnaire qui est fourni pour les marqueurs dont glyphes prennent en charge le glisser-déplacer. Un glyphe est une icône qui indique la position d’un marqueur.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Retourne un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interface à partir d’un service qui fournit un texte marqueurs aux autres VSPackages.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Permet d’accéder à et ajuste la position d’un marqueur de texte dans une mémoire tampon de texte à l’aide des coordonnées unidimensionnelles. S’il est possible, n’utilisez pas cette interface.

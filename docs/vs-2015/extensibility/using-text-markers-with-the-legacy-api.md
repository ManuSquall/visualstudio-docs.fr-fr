---
title: Utilisation des marqueurs de texte avec l’API héritée | Microsoft Docs
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
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695476"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Utilisation de marqueurs de texte avec l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un marqueur de texte est une plage de texte flottante dans une mémoire tampon qui peut affecter l’affichage et le comportement d’une zone de texte. Les marqueurs incluent des points d’arrêt, des signets, des traits de soulignement ondulés et des zones en lecture seule. Les marqueurs de texte sont fondamentalement différents de la coloration syntaxique. La coloration de la syntaxe est un moyen rapide de communiquer la syntaxe de langage associée à une région de texte. La coloration de la syntaxe est généralement demandée lorsque Windows repeint l’écran, lorsque la vitesse est importante. La coloration de la syntaxe modifie uniquement la couleur du texte. Les marqueurs de texte peuvent modifier de nombreuses autres propriétés de texte. Les marqueurs de texte peuvent « flotter » et appliquer un comportement et des couleurs spéciaux.  
  
 En raison de la surcharge de performance associée aux marqueurs de texte, ne créez pas de marqueurs pour vos mémoires tampons de texte. Chaque marqueur est mis à jour chaque fois qu’un utilisateur modifie le contenu de la mémoire tampon.  
  
> [!NOTE]
> Les utilisateurs peuvent modifier la couleur d’un type de marqueur visible, mais pas sa forme et son style. Pour plus d’informations, consultez [polices et couleurs, environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour ajouter des marqueurs de texte standard](../extensibility/how-to-add-standard-text-markers.md)|Décrit comment ajouter un type de marqueur de texte standard fourni par l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur principal à un affichage de texte.|  
|[Guide pratique pour implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)|Décrit comment implémenter une instance du [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] marqueur qui est utilisé pour indiquer des erreurs à l’aide de soulignements ondulés rouges.|  
|[Guide pratique pour créer des marqueurs de texte personnalisés](../extensibility/how-to-create-custom-text-markers.md)|Décrit comment créer et ajouter un type de marqueur de texte personnalisé à un affichage de texte.|  
|[Guide pratique pour utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)|Explique comment ajouter des marqueurs de texte.|  
|[À l’intérieur de l’éditeur de base](../extensibility/inside-the-core-editor.md)|Décrit les fonctionnalités de l’éditeur principal et fournit des détails sur la personnalisation de l’éditeur principal.|  
|[Fonctionnalités de l’éditeur](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Décrit les fonctionnalités disponibles dans l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur principal.|  
  
## <a name="reference"></a>Informations de référence  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Fournit un mécanisme uniforme pour obtenir des informations sur un type de marqueur de texte spécifique, qu’il soit prédéfini par l’éditeur ou enregistré par un VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Donne accès à et ajuste la position d’un marqueur de texte dans une mémoire tampon de texte à l’aide de coordonnées à deux dimensions.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Fournit des méthodes pour gérer des marqueurs de texte.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Fournit des rappels à l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE et à d’autres processus utilisés pour ajuster un marqueur de texte.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Étend les fonctionnalités disponibles via l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface en fournissant des rappels supplémentaires.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Étend les fonctionnalités disponibles via l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface en fournissant des rappels supplémentaires.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Permet à un type de marqueur de déterminer si d’autres types de marqueur partagent le même jeu de couleurs.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Fournit le contexte pour les marqueurs de texte de l'éditeur principal. Pour chaque type de marqueur de texte qui se trouve dans l’éditeur principal, l’IDE crée un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> objet distinct.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Gestionnaire fourni pour les marqueurs dont les glyphes prennent en charge la modification par glisser-déplacer. Un glyphe est une icône qui indique la position d’un marqueur.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Retourne une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interface à partir d’un service qui fournit des marqueurs de texte à d’autres VSPackages.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Donne accès à et ajuste la position d’un marqueur de texte dans une mémoire tampon de texte à l’aide de coordonnées unidimensionnelles. Si possible, n’utilisez pas cette interface.

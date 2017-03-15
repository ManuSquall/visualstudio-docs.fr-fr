---
title: "&#192; l&#39;aide de marqueurs de texte avec l&#39;API h&#233;rit&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - marqueurs de texte"
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# &#192; l&#39;aide de marqueurs de texte avec l&#39;API h&#233;rit&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

un marqueur de texte est une plage flottante de texte dans une mémoire tampon qui peut affecter l'affichage et le comportement d'une zone de texte.  Le incluent des points d'arrêt, les signets, des lignes ondulées, et de zones en lecture seule.  les marqueurs de texte sont fondamentalement différents de la coloration de syntaxe.  La coloration de syntaxe est un moyen rapide de transmettre la syntaxe du langage qui est associée à une zone de texte.  La coloration de syntaxe est généralement demandée lors de les fenêtres redessine l'écran, lorsque la vitesse est important.  La coloration de syntaxe modifie uniquement la couleur du texte.  Les marqueurs de texte peuvent modifier de nombreuses autres propriétés de texte.  Les marqueurs de texte peuvent « float » et appliquez le comportement et la coloration spéciaux.  
  
 En raison de la surcharge de performance associée à des marqueurs de texte, ne créez pas plusieurs marqueurs pour les mémoires tampons de texte.  Chaque marque est mise à jour chaque fois qu'un utilisateur modifie le contenu de la mémoire tampon.  
  
> [!NOTE]
>  Les utilisateurs peuvent modifier la couleur d'un type de marqueur visible mais pas sa forme et de style.  Pour plus d'informations, consultez [Polices et couleurs, Environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md)|Décrit comment ajouter un type standard de marqueur de texte fourni par l'éditeur principal de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à un affichage de texte.|  
|[Comment : implémenter des marqueurs d'erreur](../extensibility/how-to-implement-error-markers.md)|Décrit comment implémenter une instance de la marque de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui est utilisée pour indiquer des erreurs à l'aide de les lignes ondulées rouges.|  
|[Comment : créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)|décrit comment créer et ajouter un type personnalisé de marqueur de texte à un affichage de texte.|  
|[Comment : utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)|explique comment ajouter des marqueurs de texte.|  
|[Dans l'éditeur de base](../extensibility/inside-the-core-editor.md)|Décrit les fonctionnalités du éditeur principal et fournit des détails sur la personnalisation de l'éditeur principal.|  
|[Editor Features](http://msdn.microsoft.com/fr-fr/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Décrit les fonctionnalités disponibles dans l'éditeur principal de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .|  
  
## Référence  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Fournit un mécanisme uniforme pour obtenir des informations sur un type spécifique de marqueur de texte, si prédéfini par l'éditeur ou stocké par un VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Fournit l'accès à et ajustez la position d'un marqueur de texte dans une mémoire tampon de texte à l'aide de les coordonnées à deux dimensions.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 fournit des méthodes pour gérer des marqueurs de texte.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Fournit les rappels à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'IDE et d'autres processus utilisés pour ajuster un marqueur de texte.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Étend les fonctionnalités disponibles via l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> en fournissant des rappels supplémentaires.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Étend les fonctionnalités disponibles via l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> en fournissant des rappels supplémentaires.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Permet à un type de marqueur pour déterminer si d'autres types de marqueur partagent le même jeu de couleurs.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Fournit des informations de contexte pour les marqueurs de texte dans l'éditeur principal.  Pour chaque type de marqueur de texte situé dans l'éditeur principal, l'IDE crée un objet distinct d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> .  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Un gestionnaire qui est fourni pour les marqueurs dont les glyphes prennent en charge la modification par glisser\-déplacer.  Un glyphe est une icône qui indique la position de marque.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Retourne une interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> d'un service qui fournit des marqueurs de texte à l'autre des VSPackages.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Fournit l'accès à et ajustez la position d'un marqueur de texte dans une mémoire tampon de texte à l'aide de les coordonnées unidimensionnelles.  Si possible, n'utilisez pas cette interface.
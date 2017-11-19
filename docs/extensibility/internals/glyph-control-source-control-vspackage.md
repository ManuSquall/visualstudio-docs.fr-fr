---
title: "Contrôle de glyphe (VSPackage de contrôle de code Source) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ac7839d4d7456f28d7e4b5b8ecd4096904dce38e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="glyph-control-source-control-vspackage"></a>Contrôle de glyphe (VSPackage de contrôle de code Source)
Partie de l’intégration en profondeur disponible pour les VSPackages de contrôle de code source est la capacité à afficher leurs propres glyphes pour indiquer l’état des éléments sous contrôle de code source.  
  
## <a name="levels-of-glyph-control"></a>Niveaux de contrôle de glyphe  
 Un glyphe de l’état est une icône qui indique l’état actuel d’un élément lors de l’affiche, par exemple dans **l’Explorateur de solutions** ou dans **affichage de classes**. Un contrôle de code source VSPackage peut exercer à deux niveaux de contrôle de glyphe. Il peut limiter le choix de glyphes à un ensemble prédéfini de glyphes fournie par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, ou il peut définir un jeu personnalisé de glyphes à afficher.  
  
### <a name="default-set-of-glyphs"></a>Jeu de glyphes par défaut  
 Pour déterminer les glyphes d’état qui sont associés à un élément dans **l’Explorateur de solutions**, un projet demande le glyphe d’état à partir du contrôle de code source à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Un contrôle de code source VSPackage peut décider de conserver le choix des glyphes limité aux glyphes prédéfinies fournies par l’IDE. Dans ce cas, le VSPackage retransmettre un tableau de valeurs représentant les énumérations de glyphe qui sont définies dans vsshell.idl. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Il s’agit d’un ensemble prédéfini de glyphes définie par l’IDE, par exemple un verrou pour le glyphe « Archivé » et une case à cocher que le glyphe de « Extrait ».  
  
### <a name="custom-set-of-glyphs"></a>Un ensemble de glyphes personnalisés  
 Un contrôle de code source VSPackage pouvez utiliser ses propres glyphes pour une unique « apparence » lorsqu’il est installé. Lorsqu’un contrôle de code source nouveau VSPackage est active, elle doit être en mesure de démarrer à l’aide de son propre glyphes même si une source précédente contrôle VSPackage est toujours chargé mais inactive. Dans ce mode, le contrôle de code source VSPackage pouvez toujours utiliser les icônes existantes afin de conserver une apparence cohérente avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si elle choisit.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service prend en charge une interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, qui peut implémenter le VSPackage et qui sera demandé par l’IDE. Lors de l’IDE effectue une demande, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à son tour essaient de cette interface à partir du contrôle de source actuellement inscrite VSPackage. Si l’interface existe dans le VSPackage inscrit, la demande de l’IDE de glyphes personnalisés réussit ; dans le cas contraire, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE utilise le jeu de glyphes par défaut.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> méthode est utilisée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour obtenir une liste des images montrant le contrôle de code source différents états. Le contrôle de code source VSPackage retourne à l’IDE un handle vers la liste d’images pour ses glyphes personnalisés. L’IDE effectue une copie de la liste d’images à ce stade et il utilise ultérieurement pour choisir les glyphes à afficher. Si la nouvelle interface n’est pas prise en charge ou `IVsSccGlyphs::GetCustomGlyphList` méthode retourne E_NOTIMPL, puis l’IDE obtient ses glyphes dans la liste par défaut des glyphes fourni par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
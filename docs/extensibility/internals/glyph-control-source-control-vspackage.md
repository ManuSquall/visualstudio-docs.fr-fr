---
title: Contrôle de glyphe (VSPackage de contrôle de code Source) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d30682a85551aab062824688b635260c30df63f9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321345"
---
# <a name="glyph-control-source-control-vspackage"></a>Contrôle de glyphe (VSPackage de contrôle source)
Partie de l’intégration approfondie disponible pour les VSPackages de contrôle de code source est la capacité d’afficher leurs propres glyphes pour indiquer l’état des éléments sous contrôle de code source.

## <a name="levels-of-glyph-control"></a>Niveaux de contrôle de glyphe
 Un glyphe de l’état est une icône qui indique l’état actuel de l’élément affiché, par exemple dans **l’Explorateur de solutions** ou dans **affichage de classes**. Un VSPackage de contrôle de code source peut exercer deux niveaux de contrôle de glyphe. Il peut limiter le choix de glyphes à un ensemble prédéfini de glyphes fournies par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, ou il peut définir un jeu personnalisé de glyphes à afficher.

### <a name="default-set-of-glyphs"></a>Ensemble de glyphes par défaut
 Pour déterminer les glyphes d’état qui sont associés à un élément dans **l’Explorateur de solutions**, un projet demande le glyphe de l’état de contrôle de code source à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Un contrôle de code source VSPackage peut décider de conserver le choix de glyphes limitée aux glyphes prédéfinies fournies par l’IDE. Dans ce cas, le VSPackage retransmet un tableau de valeurs représentant les énumérations de glyphe qui sont définies dans *vsshell.idl*. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Il s’agit d’un ensemble prédéfini de glyphes définie par l’IDE, comme un verrou pour le glyphe archivé et une case à cocher pour le glyphe extrait.

### <a name="custom-set-of-glyphs"></a>Jeu de glyphes personnalisé
 Un VSPackage de contrôle de code source peut utiliser son propre glyphes pour un aspect unique lorsqu’il est installé. Lorsqu’un contrôle de code source nouveau VSPackage est actif, il doit être en mesure de démarrer à l’aide de son propre glyphes même si le VSPackage de contrôle du code source précédente est toujours chargé mais inactive. Dans ce mode, le VSPackage de contrôle de code source toujours pouvez utiliser les icônes existants afin de conserver une apparence cohérente avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si elle choisit.

 Le <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service prend en charge une interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, ce qui le VSPackage peut éventuellement implémenter et qui sera demandé par l’IDE. Lorsque l’IDE effectue une requête, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à son tour essaient de cette interface à partir du contrôle de source actuellement inscrite VSPackage. Si l’interface existe dans le VSPackage inscrit, la demande de l’IDE de glyphes personnalisés réussit ; Sinon, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE utilise son jeu de glyphes par défaut.

 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> méthode est utilisée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour obtenir une liste des images montrant le contrôle de code source différents états. Le contrôle de code source VSPackage retourne à l’IDE un handle vers la liste d’images pour des glyphes personnalisés. L’IDE effectue une copie de la liste d’images à ce stade et utilise plus tard pour choisir les glyphes à afficher. Si la nouvelle interface n’est pas pris en charge ou la `IVsSccGlyphs::GetCustomGlyphList` retourne de la méthode `E_NOTIMPL`, puis l’IDE obtient ses glyphes dans la liste par défaut de glyphes fourni par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
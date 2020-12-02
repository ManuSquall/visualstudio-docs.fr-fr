---
title: Contrôle Glyph (VSPackage de contrôle de code source) | Microsoft Docs
description: Découvrez comment afficher des glyphes personnalisés dans un VSPackage de contrôle de code source afin de pouvoir utiliser vos propres icônes pour indiquer l’état des éléments sous contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eaf7f40224e2f197627bb995dc6cccdf297b46e5
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480471"
---
# <a name="glyph-control-source-control-vspackage"></a>Contrôle Glyph (VSPackage de contrôle de code source)
Une partie de l’intégration profonde disponible pour les VSPackages de contrôle de code source est la possibilité d’afficher leurs propres glyphes pour indiquer l’état des éléments sous contrôle de code source.

## <a name="levels-of-glyph-control"></a>Niveaux de contrôle de glyphe
 Un glyphe d’État est une icône qui indique l’état actuel d’un élément lorsqu’il est affiché, par exemple dans **Explorateur de solutions** ou dans **affichage de classes**. Un VSPackage de contrôle de code source peut exercer deux niveaux de contrôle de glyphe. Il peut limiter le choix des glyphes à un ensemble prédéfini de glyphes fournis par l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, ou il peut définir un ensemble personnalisé de glyphes à afficher.

### <a name="default-set-of-glyphs"></a>Jeu de glyphes par défaut
 Pour déterminer les glyphes d’État associés à un élément dans **Explorateur de solutions**, un projet demande le glyphe d’État à partir du contrôle de code source à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . Un VSPackage de contrôle de code source peut décider de conserver le choix des glyphes limités aux glyphes prédéfinis fournis par l’IDE. Dans ce cas, le VSPackage passe un tableau de valeurs représentant les énumérations de glyphes définies dans *vsshell. idl*. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Il s’agit d’un jeu prédéfini de glyphes défini par l’IDE, tel qu’un cadenas pour le glyphe archivé, et une coche pour le glyphe extrait.

### <a name="custom-set-of-glyphs"></a>Ensemble personnalisé de glyphes
 Un VSPackage de contrôle de code source peut utiliser ses propres glyphes pour une apparence et une convivialité uniques lorsqu’il est installé. Quand un nouveau VSPackage de contrôle de code source est actif, il doit pouvoir commencer à utiliser ses propres glyphes même si un VSPackage de contrôle de code source précédent est toujours chargé, mais inactif. Dans ce mode, le VSPackage de contrôle de code source peut toujours utiliser les icônes existantes afin de conserver une apparence cohérente avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si elle le souhaite.

 Le <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service prend en charge une interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> , que le VSPackage peut éventuellement implémenter et qui seront demandés par l’IDE. Lorsque l’IDE émet une demande, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] essaie à son tour d’obtenir cette interface à partir du VSPackage de contrôle de code source actuellement inscrit. Si l’interface existe dans le VSPackage inscrit, la requête de l’IDE pour les glyphes personnalisés est réussie. dans le cas contraire, l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE utilise son ensemble de glyphes par défaut.

 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> méthode est utilisée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour obtenir une liste d’images présentant divers États de contrôle de code source. Le VSPackage de contrôle de code source retourne à l’IDE un handle vers la liste d’images pour ses glyphes personnalisés. L’IDE effectue une copie de la liste d’images à ce stade et l’utilise ultérieurement pour choisir les glyphes à afficher. Si la nouvelle interface n’est pas prise en charge ou si la `IVsSccGlyphs::GetCustomGlyphList` méthode retourne `E_NOTIMPL` , l’IDE obtient ses glyphes à partir de la liste par défaut des glyphes fournis par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

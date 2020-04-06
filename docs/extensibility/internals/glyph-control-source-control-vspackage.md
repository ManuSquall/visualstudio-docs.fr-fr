---
title: Contrôle de Glyph (Contrôle source VSPackage) Microsoft Docs
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
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708317"
---
# <a name="glyph-control-source-control-vspackage"></a>Contrôle de Glyph (contrôle source VSPackage)
Une partie de l’intégration profonde disponible pour le contrôle des sources VSPackages est la possibilité d’afficher leurs propres glyphes pour indiquer l’état des éléments sous contrôle source.

## <a name="levels-of-glyph-control"></a>Niveaux de contrôle du glyphe
 Un glyphe d’état est une icône qui indique l’état actuel d’un élément lorsqu’il est affiché, par exemple dans **Solution Explorer** ou dans **Class View**. Un contrôle source VSPackage peut exercer deux niveaux de contrôle du glyphe. Il peut limiter le choix des glyphes à un ensemble prédéfini de glyphes fournis par l’IDE, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ou il peut définir un ensemble personnalisé de glyphes à afficher.

### <a name="default-set-of-glyphs"></a>Ensemble par défaut de glyphes
 Pour déterminer les glyphes d’état qui sont associés à un élément dans **Solution** <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>Explorer , un projet demande le glyphe de l’état de contrôle source en utilisant le . Un contrôle source VSPackage peut décider de garder le choix des glyphes limité aux glyphes prédéfinis fournis par l’IDE. Dans ce cas, le VSPackage transmet un tableau de valeurs représentant les énumérations de glyphe qui sont définies dans *vsshell.idl*. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Il s’agit d’un ensemble prédéfini de glyphes définis par l’IDE, comme un cadenas pour le glyphe enregistré, et une marque de contrôle pour le glyphe vérifié.

### <a name="custom-set-of-glyphs"></a>Ensemble personnalisé de glyphes
 Un contrôle source VSPackage peut utiliser ses propres glyphes pour un look unique et se sentir quand il est installé. Lorsqu’un nouveau contrôle source VSPackage est actif, il devrait être en mesure de commencer à utiliser ses propres glyphes, même si un contrôle source précédent VSPackage est toujours chargé, mais inactif. Dans ce mode, le contrôle source VSPackage peut toujours utiliser les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] icônes existantes afin de maintenir un look compatible avec si elle le souhaite.

 Le <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service prend <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>en charge une interface, que le VSPackage peut implémenter d’option et qui sera demandée par l’IDE. Lorsque l’IDE fait [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] une demande, essayera à son tour d’obtenir cette interface à partir du contrôle source actuellement enregistré VSPackage. Si l’interface existe dans le VSPackage enregistré, la demande d’IDE pour les glyphes personnalisés réussit; autrement, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’IDE utilise son ensemble par défaut de glyphes.

 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> méthode est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisée pour obtenir une liste d’images montrant divers états de contrôle des sources. Le contrôle source VSPackage retourne à l’IDE une poignée à la liste d’images pour ses glyphes personnalisés. L’IDE fait une copie de la liste d’images à ce stade et l’utilise plus tard pour choisir les glyphes à afficher. Si la nouvelle interface n’est pas prise en charge ou la `IVsSccGlyphs::GetCustomGlyphList` méthode revient `E_NOTIMPL`, puis [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]l’IDE obtient ses glyphes de la liste par défaut de glyphes fournis par .

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

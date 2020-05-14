---
title: 'Comment : Soutenir l’énoncé dans un service de langue héritée (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707916"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Comment : Soutien dans un service linguistique hérité
La description est utilisée pour étendre ou effondrer différentes régions de texte. La façon d’être utilisée peut être définie différemment par différentes langues. Pour plus d’informations, voir [Mode Plan](../../ide/outlining.md).

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon de mettre en œuvre la mise en œuvre de la mise en œuvre, voir [Procédure Pas à pas: Outlineing](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

 Ce qui suit montre comment soutenir cette commande pour votre service linguistique.

## <a name="to-support-outlining"></a>Pour soutenir la mise en avant

1. Implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> votre objet de service linguistique.

2. Faites <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> appel à l’objet actuel de la session de mise en scène pour ajouter de nouvelles régions à contours.

## <a name="robust-programming"></a>Programmation fiable
 Lorsqu’un utilisateur sélectionne **Collapse To Definitions** sur le menu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> **Outlining,** l’IDE fait appel à votre service linguistique.

 Lorsque cette méthode est appelée, l’IDE passe dans un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> pointeur (un pointeur à un tampon de texte) et un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (un pointeur à la session de mise en ligne en cours).

 Vous pouvez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> appeler la méthode pour plusieurs régions `rgOutlnReg` à contours en spécifiant ces régions dans le paramètre. Le `rgOutlnReg` paramètre <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> est une structure. Ce processus vous permet de spécifier différentes caractéristiques de la région cachée, comme l’élargissement ou l’effondrement d’une région particulière.

> [!NOTE]
> Faites attention à cacher des personnages de nouvelle ligne. Le texte caché doit s’étendre du début de la première ligne au dernier caractère de la dernière ligne dans une section, laissant visible le caractère final de nouvelle ligne.

## <a name="see-also"></a>Voir aussi
- [Comment : Fournir un support texte caché dans un service linguistique hérité](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Comment : Fournir un soutien élargi dans un service linguistique hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

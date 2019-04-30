---
title: 'Procédure : Prend en charge le mode plan dans un Service de langage hérité | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3181f7ab2e69dd04a21f5f81ca470f849c268e03
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418384"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Procédure : Prend en charge le mode plan dans un service de langage hérité
Le mode plan est utilisé pour développer ou réduire des différentes régions du texte. Le moyen le mode plan est utilisé peut être défini différemment par différents langages. Pour plus d’informations, voir [Mode Plan](../../ide/outlining.md).

 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter le mode plan, consultez [procédure pas à pas : Mode Plan](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.

 Ce qui suit montre comment prendre en charge de cette commande pour votre service de langage.

## <a name="to-support-outlining"></a>Pour prendre en charge le mode plan

1. Implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> sur votre objet de service de langage.

2. Appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> sur l’objet de session en mode plan actuel pour ajouter de nouvelles régions en mode plan.

## <a name="robust-programming"></a>Programmation fiable
 Lorsqu’un utilisateur sélectionne **réduire aux définitions** sur le **mode plan** menu, les appels IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> sur votre service de langage.

 Lorsque cette méthode est appelée, l’IDE passe un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> pointeur (il s’agit d’un pointeur vers une mémoire tampon de texte) et un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (il s’agit d’un pointeur vers la session active en mode plan).

 Vous pouvez appeler la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> méthode pour plusieurs régions en mode plan en spécifiant ces régions dans le `rgOutlnReg` paramètre. Le `rgOutlnReg` paramètre est un <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> structure. Ce processus vous permet de spécifier des caractéristiques différentes de la zone masquée, telles que si une région particulière est développée ou réduite.

> [!NOTE]
> Soyez prudent sur le masquage des caractères de nouvelle ligne. Texte masqué est souhaitable d’étendre à partir du début de la première ligne au dernier caractère de la dernière ligne dans une section, en laissant le caractère de nouvelle ligne final est visible.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Fournir la prise en charge de texte masqué dans un service de langage hérité](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Guide pratique pour Fournir une prise en charge étendue de mode plan dans un service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
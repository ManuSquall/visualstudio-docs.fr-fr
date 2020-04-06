---
title: Mise en œuvre de la coloration Syntaxe (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707648"
---
# <a name="implementing-syntax-coloring"></a>Implémentation de la coloration de syntaxe
Lorsque le service linguistique fournit une colorisation syntaxe, le parseur convertit une ligne de texte en une gamme d’éléments colorables et retourne les types de jetons correspondant à ces éléments colorables. Le parseur doit retourner les types de jetons qui appartiennent à une liste d’articles colorables. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]affiche chaque élément colorable dans la fenêtre de code en fonction des attributs attribués par l’objet colorant au type de jeton approprié.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ne spécifie pas une interface d’analyse, et l’implémentation d’analyse est complètement à vous. Toutefois, une implémentation d’analyse par défaut est fournie dans le projet Visual Studio Language Package. Pour le code géré, le cadre de paquet géré (MPF) fournit un support complet pour la colorisation du texte.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter la coloration syntaxe, voir [Procédure Pas à pas: Mise en évidence du texte](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Étapes suivies d’un éditeur pour coloriser le texte

1. L’éditeur obtient le coloriant en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode sur l’objet. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

2. L’éditeur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> appelle la méthode pour déterminer si le colorateur a besoin de l’état de chaque ligne pour être maintenu en dehors du colorisier.

3. Si le colorateur exige que l’état soit maintenu en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> dehors du colorisier, l’éditeur appelle la méthode pour obtenir l’état de la première ligne.

4. Pour chaque ligne dans le tampon, l’éditeur appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode, qui effectue les étapes suivantes:

    1. La ligne de texte est passée à un scanner pour convertir le texte en jetons. Chaque jeton spécifie le texte symbolique et le type de jeton.

    2. Le type de jeton est converti en un index en une liste d’éléments colorables.

    3. L’information symbolique est utilisée pour remplir un tableau de telle sorte que chaque élément de la gamme correspond à un personnage dans la ligne. Les valeurs stockées dans le tableau sont les index dans la liste des éléments colorables.

    4. L’état à la fin de la ligne est retourné pour chaque ligne.

5. Si le colorateur exige que l’état soit maintenu, l’éditeur cache l’état pour cette ligne.

6. L’éditeur rend la ligne de texte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> à l’aide des informations retournées de la méthode. Ce processus implique les étapes suivantes :

    1. Pour chaque personnage de la ligne, obtenez l’index d’élément colorable.

    2. Si vous utilisez les éléments colorables par défaut, accédez à la liste d’éléments colorables de l’éditeur.

    3. Sinon, appelez la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> du service linguistique pour obtenir un article colorable.

    4. Utilisez les informations contenues dans l’élément colorable pour rendre le texte dans l’écran.

## <a name="managed-package-framework-colorizer"></a>Coloriage de cadre de paquet géré
 Le cadre de paquet géré (MPF) fournit toutes les classes qui sont nécessaires pour mettre en œuvre un coloriseur. Votre classe de service <xref:Microsoft.VisualStudio.Package.LanguageService> linguistique devrait hériter de la classe et mettre en œuvre les méthodes requises. Vous devez fournir un scanner et un <xref:Microsoft.VisualStudio.Package.IScanner> analyseur en implémentant <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> l’interface, et retourner une instance <xref:Microsoft.VisualStudio.Package.LanguageService> de cette interface à partir de la méthode (l’une des méthodes qui doivent être mises en œuvre dans la classe). Pour plus d’informations, voir [Syntax Colorizing in a Legacy Language Service](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour utiliser des éléments coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)
- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

---
title: Implémentation de la coloration de la syntaxe | Microsoft Docs
description: Apprenez à implémenter la coloration de la syntaxe dans Visual Studio à l’aide des fonctionnalités du service de langage de Managed package Framework (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 195cf7a26b1615b7c56f3f0d06cfd9e0d44a4384
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204668"
---
# <a name="implementing-syntax-coloring"></a>Implémentation de la coloration de syntaxe
Lorsque le service de langage fournit la colorisation de syntaxe, l’analyseur convertit une ligne de texte en un tableau d’éléments coloriables et retourne des types de jetons correspondant à ces éléments coloriables. L’analyseur doit retourner les types de jetons qui appartiennent à une liste d’éléments coloriables. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] affiche chaque élément coloriable dans la fenêtre de code en fonction des attributs assignés par l’objet Coloriseur au type de jeton approprié.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne spécifie pas d’interface d’analyseur, et l’implémentation de l’analyseur vous revient entièrement. Toutefois, une implémentation de l’analyseur par défaut est fournie dans le projet de package de langage Visual Studio. Pour le code managé, Managed package Framework (MPF) fournit une prise en charge complète pour la coloration du texte.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter la coloration de la syntaxe, consultez [procédure pas à pas : mise en surbrillance du texte](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Étapes suivies par un éditeur pour colorier le texte

1. L’éditeur obtient le Coloriseur en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode sur l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objet.

2. L’éditeur appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> méthode pour déterminer si le Coloriseur a besoin de l’état de chaque ligne à conserver en dehors du Coloriseur.

3. Si le Coloriseur nécessite que l’État soit conservé en dehors du Coloriseur, l’éditeur appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> méthode pour recevoir l’état de la première ligne.

4. Pour chaque ligne de la mémoire tampon, l’éditeur appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode, qui effectue les étapes suivantes :

    1. La ligne de texte est transmise à un scanneur pour convertir le texte en jetons. Chaque jeton spécifie le texte du jeton et le type de jeton.

    2. Le type de jeton est converti en un index dans une liste d’éléments coloriables.

    3. Les informations de jeton sont utilisées pour remplir un tableau de telle sorte que chaque élément du tableau corresponde à un caractère de la ligne. Les valeurs stockées dans le tableau sont les index dans la liste des éléments coloriables.

    4. L’État à la fin de la ligne est retourné pour chaque ligne.

5. Si le Coloriseur requiert la conservation de l’État, l’éditeur met en cache l’état de cette ligne.

6. L’éditeur restitue la ligne de texte à l’aide des informations retournées par la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode. Ce processus implique les étapes suivantes :

    1. Pour chaque caractère de la ligne, récupérez l’index de l’élément coloriable.

    2. Si vous utilisez les éléments coloriables par défaut, accédez à la liste des éléments coloriés de l’éditeur.

    3. Sinon, appelez la méthode du service de langage <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> pour obtenir un élément coloriable.

    4. Utilisez les informations de l’élément coloriable pour restituer le texte dans l’affichage.

## <a name="managed-package-framework-colorizer"></a>Managed package Framework Coloriseur
 Managed package Framework (MPF) fournit toutes les classes qui sont requises pour implémenter un Coloriseur. Votre classe de service de langage doit hériter de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe et implémenter les méthodes requises. Vous devez fournir un scanneur et un analyseur en implémentant l' <xref:Microsoft.VisualStudio.Package.IScanner> interface et retourner une instance de cette interface à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> méthode (l’une des méthodes qui doivent être implémentées dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe). Pour plus d’informations, consultez [colorisation de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour utiliser des éléments coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)
- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

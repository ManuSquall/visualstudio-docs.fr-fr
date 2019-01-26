---
title: Implémentation de la coloration syntaxique | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de1a73cda8be9e56b0cad605f5507d52509ec906
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038043"
---
# <a name="implementing-syntax-coloring"></a>Implémentation de la coloration de syntaxe
Lorsque le service de langage fournit la coloration syntaxique, l’analyseur convertit une ligne de texte dans un tableau d’éléments coloriables et retourne les types de jetons correspondant à ces éléments coloriables. L’analyseur doit retourner des types de jetons qui appartiennent à une liste d’éléments coloriables. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] affiche chaque élément coloriable dans la fenêtre de code selon les attributs assignés par l’objet de Coloriseur pour le type de jeton approprié.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne spécifie pas une interface de l’analyseur, et l’implémentation de l’analyseur complètement vous revient. Toutefois, une implémentation d’analyseur par défaut est fournie dans le projet de Package de langage de Visual Studio. Pour le code managé, l’infrastructure de package managé (MPF) fournit la prise en charge complète pour la colorisation de texte.  
  
 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter la coloration de syntaxe, consultez [procédure pas à pas : Mise en surbrillance de texte](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Étapes suivies par un éditeur à mettre en couleur de texte  
  
1.  L’éditeur Obtient le Coloriseur en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objet.  
  
2.  Les appels de l’éditeur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> méthode pour déterminer si le Coloriseur doit l’état de chaque ligne à être gérés hors du Coloriseur.  
  
3.  Si le Coloriseur requiert l’état soit conservé en dehors de Coloriseur, l’éditeur appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> méthode pour obtenir l’état de la première ligne.  
  
4.  Pour chaque ligne dans la mémoire tampon, l’éditeur appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> (méthode), qui effectue les étapes suivantes :  
  
    1.  La ligne de texte est transmise à un analyseur pour convertir le texte en jetons. Chaque jeton spécifie le texte du jeton et le type de jeton.  
  
    2.  Le type de jeton est converti en un index dans une liste d’éléments coloriables.  
  
    3.  Les informations de jeton sont utilisées pour remplir un tableau où chaque élément du tableau correspond à un caractère dans la ligne. Les valeurs stockées dans le tableau sont les index dans la liste d’éléments coloriables.  
  
    4.  L’état à la fin de la ligne est retournée pour chaque ligne.  
  
5.  Si le Coloriseur requiert l’état soit conservé, l’éditeur met en cache l’état de cette ligne.  
  
6.  L’éditeur affiche la ligne de texte en utilisant les informations retournées par le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> (méthode). Ce processus implique les étapes suivantes :  
  
    1.  Pour chaque caractère de la ligne, obtenir l’index de l’élément coloriable.  
  
    2.  Si vous utilisez les éléments coloriables par défaut, accéder à liste d’éléments coloriables de l’éditeur.  
  
    3.  Sinon, appelez le service de langage <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> méthode pour obtenir un élément coloriable.  
  
    4.  Utilisez les informations de l’élément coloriable à restituer le texte dans l’affichage.  
  
## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Coloriseur  
 L’infrastructure de package managé (MPF) fournit toutes les classes qui sont requis pour implémenter un Coloriseur. Votre classe de service de langage doit hériter la <xref:Microsoft.VisualStudio.Package.LanguageService> classe et implémenter les méthodes obligatoires. Vous devez fournir un scanneur et l’analyseur en implémentant la <xref:Microsoft.VisualStudio.Package.IScanner> interface et retourner une instance de cette interface à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (méthode) (une des méthodes qui doivent être implémentées dans le <xref:Microsoft.VisualStudio.Package.LanguageService> classe). Pour plus d’informations, consultez [couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Utiliser des éléments Coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Éléments Coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)   
 [Développement d’un Service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
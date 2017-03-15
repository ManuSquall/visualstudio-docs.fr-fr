---
title: "L’implémentation de la coloration de syntaxe | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 67535bcc2c907978c24d764c617f8311dc51a444
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-syntax-coloring"></a>L’implémentation de la coloration de syntaxe
Lorsque le service de langage fournit la coloration de syntaxe, l’analyseur convertit une ligne de texte dans un tableau de couleurs et retourne les types de jetons correspondant à ces éléments coloriable. L’analyseur doit retourner les types de jetons qui appartiennent à une liste de propriétés. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]affiche chaque élément coloriable dans la fenêtre de code selon les attributs affectés par l’objet Coloriseur pour le type de jeton approprié.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ne spécifie pas une interface de l’analyseur et mise en œuvre de l’analyseur est complètement vous appartient. Toutefois, une implémentation d’analyseur par défaut est fournie dans le projet de Package de langue de Visual Studio. Pour le code managé, l’infrastructure du package managé (MPF) prend complètement en charge la colorisation de texte.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter la coloration de syntaxe, consultez [procédure pas à pas : mise en surbrillance de texte](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Étapes suivies par un éditeur pour colorer le texte  
  
1.  L’éditeur Obtient le Coloriseur en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>objet.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>  
  
2.  Les appels de l’Éditeur du <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>méthode pour déterminer si le Coloriseur a besoin de l’état de chaque ligne peut être géré en dehors de la Coloriseur.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>  
  
3.  Si le Coloriseur requiert l’état peut être géré en dehors de la Coloriseur, l’éditeur appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>méthode pour obtenir l’état de la première ligne.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>  
  
4.  Pour chaque ligne dans la mémoire tampon, appelle l’éditeur de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>méthode qui effectue les étapes suivantes :</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
    1.  La ligne de texte est transmise à un analyseur pour convertir le texte en jetons. Chaque jeton spécifie le texte de jeton et le type de jeton.  
  
    2.  Le type de jeton est converti en un index dans une liste de propriétés.  
  
    3.  Les informations de jeton sont utilisées pour remplir un tableau où chaque élément du tableau correspond à un caractère de la ligne. Les valeurs stockées dans le tableau sont les index dans la liste de propriétés.  
  
    4.  L’état à la fin de la ligne est retourné pour chaque ligne.  
  
5.  Si le Coloriseur requiert l’état soit conservé, l’éditeur met en cache l’état de cette ligne.  
  
6.  L’éditeur affiche la ligne de texte en utilisant les informations retournées par la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>méthode.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Ce processus implique les étapes suivantes :  
  
    1.  Pour chaque caractère de la ligne, obtenir l’index de l’élément coloriable.  
  
    2.  Si vous utilisez les éléments pouvant être en couleur par défaut, accéder à liste des propriétés de l’éditeur.  
  
    3.  Sinon, appelez le service de langage <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>méthode pour obtenir un élément coloriable.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>  
  
    4.  Utilisez les informations de l’élément coloriable pour afficher le texte dans l’affichage.  
  
## <a name="managed-package-framework-colorizer"></a>Package managé Framework Coloriseur  
 L’infrastructure du package managé (MPF) fournit toutes les classes qui sont requises pour implémenter un Coloriseur. Votre classe de service de langage doit hériter de la <xref:Microsoft.VisualStudio.Package.LanguageService>classe et implémenter les méthodes obligatoires.</xref:Microsoft.VisualStudio.Package.LanguageService> Vous devez fournir un scanneur et l’analyseur en implémentant le <xref:Microsoft.VisualStudio.Package.IScanner>d’interface et retourner une instance de cette interface à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>(méthode) (une des méthodes qui doivent être implémentées dans la <xref:Microsoft.VisualStudio.Package.LanguageService>classe).</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> </xref:Microsoft.VisualStudio.Package.IScanner> Pour plus d’informations, consultez [coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : utiliser des éléments coloriable intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Éléments coloriable personnalisés](../../extensibility/internals/custom-colorable-items.md)   
 [Développement d’un Service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

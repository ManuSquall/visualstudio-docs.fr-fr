---
title: Saisie semi-automatique des instructions dans un Service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0310f515a444d0ff68fe971463602c484763848b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965677"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Saisie semi-automatique des instructions dans un service de langage hérité
Saisie semi-automatique des instructions sont le processus par lequel le service de langage permet aux utilisateurs de terminer un mot clé du langage ou un élément qu’il démarre en tapant dans l’éditeur principal. Cette rubrique explique le fonctionnement de la saisie semi-automatique des instructions et comment l’implémenter dans votre service de langage.  
  
 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter la saisie semi-automatique des instructions, consultez [procédure pas à pas : Affichage de saisie semi-automatique des instructions](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="implementing-statement-completion"></a>Implémentation de saisie semi-automatique des instructions  
 Dans l’éditeur principal, la saisie semi-automatique des instructions Active une interface utilisateur spéciale qui interactive vous permet plus facilement et rapidement écrire du code. Saisie semi-automatique des instructions vous aide à en affichant les objets pertinentes ou des classes lorsqu’ils sont nécessaires, ce qui vous évite d’avoir à mémoriser des éléments spécifiques ou avoir à les rechercher dans une rubrique de référence.  
  
 Pour implémenter la saisie semi-automatique des instructions, votre langage doit avoir un déclencheur d’achèvement instruction, qui peut être analysé. Par exemple, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] utilise un opérateur point (.), tandis que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] utilise une flèche (->) opérateur. Un service de langage peut utiliser plus d’un déclencheur pour initier la saisie semi-automatique des instructions. Ces déclencheurs sont programmés dans le filtre de commande.  
  
## <a name="command-filters-and-triggers"></a>Filtres de commande et des déclencheurs  
 Commandes filtres interceptent les occurrences de votre déclencheur ou de déclencheurs. Pour ajouter le filtre de commande à la vue, implémentez le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> d’interface et l’attacher à la vue en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (méthode). Vous pouvez utiliser le même filtre de commande (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) pour tous les aspects de votre service de langage, telles que la saisie semi-automatique des instructions, les marqueurs d’erreur et les conseils de méthode. Pour plus d’informations, consultez [commandes de Service de langage hérité interception](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Lorsque le déclencheur est entré dans l’éditeur, en particulier, la mémoire tampon de texte, votre service de langage appelle ensuite la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> (méthode). Cela entraîne l’éditeur afficher l’interface utilisateur afin que l’utilisateur peut choisir parmi les candidats de saisie semi-automatique d’instruction. Cette méthode vous oblige à implémenter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> et <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> indicateurs en tant que paramètres. La liste des éléments de saisie semi-automatique s’affiche dans une zone de liste déroulante. Comme l’utilisateur poursuit la saisie, la sélection dans la zone de liste est mise à jour pour refléter que la correspondance la plus proche aux plus récente caractères tapé. L’éditeur principal implémente l’interface utilisateur pour la saisie semi-automatique des instructions, mais le service de langage doit implémenter le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface pour définir un ensemble d’éléments de saisie semi-automatique de candidat pour l’instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [Interception des commandes du service de langage hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
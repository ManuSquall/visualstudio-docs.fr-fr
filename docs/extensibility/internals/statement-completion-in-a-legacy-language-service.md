---
title: Saisie semi-automatique des instructions dans un Service de langage hérité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d76face8f43bcb428a9c3b997083f8299d332cc8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Saisie semi-automatique des instructions dans un Service de langage hérité
Saisie semi-automatique des instructions sont le processus par lequel le service de langage aide les utilisateurs à terminer un élément de qui ils ont commencé à taper dans l’éditeur principal ou le mot clé de langage. Cette rubrique explique comment fonctionnement la saisie semi-automatique des instructions et comment l’implémenter dans votre service de langage.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations sur la nouvelle façon d’implémenter la saisie semi-automatique des instructions, consultez [procédure pas à pas : affichage de saisie semi-automatique des instructions](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="implementing-statement-completion"></a>Mise en œuvre de la saisie semi-automatique des instructions  
 Dans l’éditeur principal, la saisie semi-automatique des instructions Active spéciale interface utilisateur interactive vous permet plus facilement et rapidement écrire du code. Saisie semi-automatique des instructions vous aide à en affichant des objets pertinentes ou classes lorsqu’ils sont nécessaires, ce qui vous évite d’avoir à mémoriser des éléments ou avoir à les rechercher dans une rubrique de référence.  
  
 Pour implémenter la saisie semi-automatique des instructions, votre langage doit avoir un déclencheur de saisie semi-automatique instruction, ce qui peut être analysé. Par exemple, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] utilise un opérateur point (.), tandis que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] utilise une flèche (->) (opérateur). Un service de langage peut utiliser plus d’un déclencheur pour lancer la saisie semi-automatique des instructions. Ces déclencheurs sont programmés dans le filtre de commande.  
  
## <a name="command-filters-and-triggers"></a>Filtres de commande et des déclencheurs  
 Commandes filtres interceptent les occurrences de votre déclencheur ou de déclencheurs. Pour ajouter le filtre de commande à la vue, implémentez le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de l’interface et l’associer à la vue en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (méthode). Vous pouvez utiliser le même filtre de commande (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) pour tous les aspects de votre service de langage, telles que la saisie semi-automatique des instructions, les marqueurs d’erreur et les conseils de la méthode. Pour plus d’informations, consultez [interception des commandes du Service de langage hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Lorsque le déclencheur est entré dans l’éditeur, en particulier, la mémoire tampon de texte, votre service de langage appelle ensuite le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> (méthode). Cela entraîne l’éditeur afficher l’interface utilisateur afin que l’utilisateur peut choisir parmi les candidats de fin d’instruction. Cette méthode, vous devez implémenter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> et <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> indicateurs en tant que paramètres. La liste des éléments de saisie semi-automatique s’affiche dans une zone de liste déroulante. L’utilisateur poursuit la saisie, la sélection dans la zone de liste est mis à jour pour refléter que la plus proche aux plus récente caractères typées. L’éditeur principal implémente l’interface utilisateur pour la saisie semi-automatique des instructions, mais le service de langage doit implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface pour définir un ensemble d’éléments de saisie semi-automatique candidat pour l’instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [Interception des commandes du service de langage hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
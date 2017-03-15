---
title: "Saisie semi-automatique des instructions dans un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "saisie semi-automatique des instructions"
  - "services de langage, saisie semi-automatique"
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Saisie semi-automatique des instructions dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Saisie semi\-automatique des instructions est le processus par lequel le service de langage permet aux utilisateurs de terminer un élément qui ils ont commencé à taper dans l’éditeur principal ou le mot clé de langage. Cette rubrique décrit le fonctionne de la saisie semi\-automatique des instructions et comment l’implémenter dans votre service de langage.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter la saisie semi\-automatique des instructions, consultez la page [Procédure pas à pas : Affichage de saisie semi\-automatique des instructions](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## L’implémentation de saisie semi\-automatique des instructions  
 Dans l’éditeur principal, saisie semi\-automatique active une interface utilisateur spéciale qui interactive vous permet plus facilement et rapidement écrire du code. Saisie semi\-automatique des instructions vous aide à en affichant des objets pertinentes ou classes lorsqu’ils sont nécessaires, ce qui vous évite d’avoir à mémoriser des éléments spécifiques ou les rechercher dans une rubrique de référence.  
  
 Pour implémenter la saisie semi\-automatique des instructions, votre langage doit avoir un déclencheur d’achèvement instruction, qui peut être analysé. Par exemple, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] utilise un point \(.\) opérateur, tandis que [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] utilise une flèche \(\-\>\) \(opérateur\). Un service de langage peut utiliser plus d’un déclencheur pour initier la saisie semi\-automatique des instructions. Ces déclencheurs sont programmés dans le filtre de commande.  
  
## Filtres de commande et des déclencheurs  
 Commandes filtres interceptent des occurrences de votre ou les déclencheurs. Pour ajouter le filtre de commande à la vue, implémentez le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de l’interface et l’associer à la vue en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> \(méthode\). Vous pouvez utiliser le même filtre de commande \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) pour tous les aspects de votre service de langage, telles que la saisie semi\-automatique des instructions, des marqueurs d’erreur et des conseils de méthode. Pour plus d'informations, consultez [Interception des commandes de Service de langage hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Lorsque le déclencheur est entré dans l’éditeur, en particulier, la mémoire tampon de texte, votre service de langage appelle ensuite le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> \(méthode\). Cela entraîne l’éditeur afficher l’interface utilisateur afin que l’utilisateur peut choisir parmi les candidats de fin d’instruction. Cette méthode vous oblige à implémenter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> et le <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> indicateurs en tant que paramètres. La liste des éléments de saisie semi\-automatique s’affiche dans une zone de liste déroulante. Comme l’utilisateur poursuit la saisie, la sélection dans la zone de liste est mises à jour que la plus proche aux plus récentes caractères typées. L’éditeur de base implémente l’interface utilisateur de saisie semi\-automatique des instructions, mais le service de langage doit implémenter le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface pour définir un ensemble d’éléments de saisie semi\-automatique candidat pour l’instruction.  
  
## Voir aussi  
 [Interception des commandes de Service de langage hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
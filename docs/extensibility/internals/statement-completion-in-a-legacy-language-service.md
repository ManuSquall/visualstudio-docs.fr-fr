---
title: Saisie semi-automatique des instructions dans un service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4c813052892c21a6a3e04560452b503205df117
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723221"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Saisie semi-automatique des instructions dans un service de langage hérité
La saisie semi-automatique des instructions est le processus par lequel le service de langage aide les utilisateurs à terminer un mot clé ou un élément de langage qu’ils ont commencé à taper dans l’éditeur principal. Cette rubrique décrit le fonctionnement de la saisie semi-automatique des instructions et comment l’implémenter dans votre service de langage.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter la saisie semi-automatique des instructions, consultez [procédure pas à pas : affichage de la saisie semi-automatique des instructions](../../extensibility/walkthrough-displaying-statement-completion.md)

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="implementing-statement-completion"></a>Implémentation de la saisie semi-automatique des instructions
 Dans l’éditeur de base, la saisie semi-automatique des instructions active une interface utilisateur spéciale qui vous aide à écrire du code plus facilement et plus rapidement. La saisie semi-automatique des instructions vous aide à afficher des objets ou des classes pertinents quand ils sont nécessaires, ce qui vous évite d’avoir à mémoriser des éléments spécifiques ou à les Rechercher dans une rubrique de référence de l’aide.

 Pour implémenter la saisie semi-automatique des instructions, votre langage doit avoir un déclencheur de saisie semi-automatique des instructions, qui peut être analysé. Par exemple, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] utilise un opérateur point (.), tandis que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] utilise une flèche (->). Un service de langage peut utiliser plusieurs déclencheurs pour lancer la saisie semi-automatique des instructions. Ces déclencheurs sont programmés dans le filtre de commande.

## <a name="command-filters-and-triggers"></a>Filtres et déclencheurs de commande
 Les filtres de commande interceptent les occurrences de votre déclencheur ou de vos déclencheurs. Pour ajouter le filtre de commande à la vue, implémentez l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> et attachez-la à la vue en appelant la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>. Vous pouvez utiliser le même filtre de commande (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) pour tous les aspects de votre service de langage, tels que la saisie semi-automatique des instructions, les marqueurs d’erreur et les conseils de méthode. Pour plus d’informations, consultez [interception des commandes du service de langage hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Lorsque le déclencheur est entré dans l’éditeur (plus précisément, la mémoire tampon de texte), votre service de langage appelle ensuite la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>. L’éditeur affiche alors l’interface utilisateur afin que l’utilisateur puisse choisir parmi les candidats à la saisie semi-automatique des instructions. Cette méthode exige que vous implémentiez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> et les indicateurs <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> en tant que paramètres. La liste des éléments de saisie semi-automatique s’affiche dans une zone de liste déroulante. À mesure que l’utilisateur continue à taper, la sélection dans la zone de liste est mise à jour pour refléter la correspondance la plus proche des caractères les plus récents tapés. L’éditeur principal implémente l’interface utilisateur pour la saisie semi-automatique des instructions, mais le service de langage doit implémenter l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> pour définir un ensemble d’éléments de saisie semi-automatique candidats pour l’instruction.

## <a name="see-also"></a>Voir aussi
- [Interception des commandes du service de langage hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
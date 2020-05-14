---
title: Achèvement de l’énoncé dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbeb360cf5bc0f74d6b2d9b93086382dd35da988
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704940"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Saisie semi-automatique des instructions dans un service de langage hérité
L’achèvement de l’énoncé est le processus par lequel le service linguistique aide les utilisateurs à terminer un mot clé ou un élément de langue qu’ils ont commencé à taper dans l’éditeur de base. Ce sujet traite du fonctionnement de l’achèvement des relevés et de la façon de la mettre en œuvre dans votre service linguistique.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon de mettre en œuvre l’achèvement de l’instruction, voir [Procédure pas à pas: Affichage de l’achèvement de l’instruction](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="implementing-statement-completion"></a>Achèvement de l’énoncé de mise en œuvre
 Dans l’éditeur de base, l’achèvement des relevés active une interface utilisateur spéciale qui vous aide de manière interactive à écrire plus facilement et plus rapidement du code. L’achèvement de l’énoncé aide en affichant des objets ou des classes pertinents lorsqu’ils sont nécessaires, ce qui vous évite d’avoir à vous souvenir d’éléments spécifiques ou d’avoir à les rechercher dans un sujet de référence d’aide.

 Pour mettre en œuvre l’achèvement de l’instruction, votre langue doit avoir un déclencheur d’achèvement de l’instruction, qui peut être analysé. Par exemple, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] utilise un opérateur de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] point (.) tout en utilise un opérateur de flèche (->). Un service linguistique peut utiliser plus d’un déclencheur pour initier l’achèvement de l’instruction. Ces déclencheurs sont programmés dans le filtre de commande.

## <a name="command-filters-and-triggers"></a>Filtres et déclencheurs de commande
 Les filtres de commande interceptent les occurrences de votre déclencheur ou déclencheur. Pour ajouter le filtre de commande <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> à la vue, implémentez l’interface et attachez-la à la vue en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode. Vous pouvez utiliser le<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>même filtre de commande ( ) pour tous les aspects de votre service linguistique, tels que l’achèvement des relevés, les marqueurs d’erreur et les conseils de méthode. Pour plus d’informations, voir [Intercepting Legacy Language Service Commands](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Lorsque le déclencheur est entré dans l’éditeur — en particulier, le tampon de texte — votre service linguistique appelle alors la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode. Cela amène l’éditeur à mettre en place l’interface utilisateur afin que l’utilisateur puisse choisir parmi les candidats d’achèvement de déclaration. Cette méthode vous <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> oblige <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> à implémenter et les drapeaux comme paramètres. La liste des éléments d’achèvement apparaît dans une boîte de liste de défilement. Au fur et à mesure que l’utilisateur continue de taper, la sélection dans la boîte de liste est mise à jour pour refléter la correspondance la plus proche des caractères les plus récents tapés. L’éditeur de base implémente l’interface pour <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> l’achèvement de l’instruction, mais le service linguistique doit implémenter l’interface pour définir un ensemble d’éléments d’achèvement des candidats pour la déclaration.

## <a name="see-also"></a>Voir aussi
- [Interception des commandes du service de langage hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

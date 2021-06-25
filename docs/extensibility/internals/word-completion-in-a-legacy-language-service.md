---
title: Saisie semi-automatique des mots dans un service de langage hérité | Microsoft Docs
description: La saisie semi-automatique des mots peut être prise en charge pour un service de langage hérité dans le kit de développement logiciel Visual Studio. Découvrez comment les services de langage hérités sont implémentés dans un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea386aea3a17b0fb0d93ff9872f92e86a166be5c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902629"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Saisie semi-automatique de mot dans un service de langage hérité
La saisie semi-automatique des mots remplit les caractères manquants sur un mot partiellement typé. S’il n’existe qu’une seule exécution possible, le mot est terminé lorsque vous entrez le caractère de fin. Si le mot partiel correspond à plusieurs possibilités, une liste des saisies semi-automatiques possibles s’affiche. Un caractère de fin peut être n’importe quel caractère qui n’est pas utilisé pour les identificateurs.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [extension de l’éditeur et des services de langage](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="implementation-steps"></a>Étapes d’implémentation

1. Quand l’utilisateur sélectionne **compléter le mot** dans le menu **IntelliSense** , la <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande est envoyée au service de langage.

2. La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe intercepte la commande et appelle la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode avec la raison de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. La <xref:Microsoft.VisualStudio.Package.Source> classe appelle ensuite la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode pour obtenir la liste des saisies semi-automatiques de mots possibles, puis affiche les mots dans une liste d’info-bulle à l’aide de la <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.

    S’il n’existe qu’un seul mot correspondant, la <xref:Microsoft.VisualStudio.Package.Source> classe termine le mot.

   Sinon, si le scanneur retourne la valeur du déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> lorsque le premier caractère d’un identificateur est tapé, la <xref:Microsoft.VisualStudio.Package.Source> classe détecte cela et appelle la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode avec la raison de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> . Dans ce cas, l’analyseur doit détecter la présence d’un caractère de sélection de membre et fournir une liste de membres.

## <a name="enabling-support-for-the-complete-word"></a>Activation de la prise en charge du mot complet
 Pour activer la prise en charge de la saisie semi-automatique des mots, définissez le `CodeSense` paramètre nommé passé à l' <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut User associé au package de langage. Cela définit la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriété sur la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.

 Votre analyseur doit retourner une liste de déclarations en réponse à la valeur de la raison de l’analyse <xref:Microsoft.VisualStudio.Package.ParseReason> , pour que la saisie de mot aboutisse.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implémentation du mot complet dans la méthode ParseSource
 Pour la saisie semi-automatique des mots, la <xref:Microsoft.VisualStudio.Package.Source> classe appelle la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe pour obtenir une liste des correspondances de mots possibles. Vous devez implémenter la liste dans une classe dérivée de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. <xref:Microsoft.VisualStudio.Package.Declarations>Pour plus d’informations sur les méthodes que vous devez implémenter, consultez la classe.

 Si la liste ne contient qu’un seul mot, la <xref:Microsoft.VisualStudio.Package.Source> classe insère automatiquement ce mot à la place du mot partiel. Si la liste contient plusieurs mots, la <xref:Microsoft.VisualStudio.Package.Source> classe affiche une liste d’info-bulle dans laquelle l’utilisateur peut sélectionner le choix approprié.

 Examinez également l’exemple d' <xref:Microsoft.VisualStudio.Package.Declarations> implémentation de classe en cours d' [exécution de membre dans un service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).

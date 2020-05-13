---
title: Achèvement des mots dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703176"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Saisie semi-automatique de mot dans un service de langage hérité
L’achèvement des mots remplit les caractères manquants sur un mot partiellement tapé. S’il n’y a qu’un seul achèvement possible, le mot est terminé lorsque le caractère d’achèvement est entré. Si le mot partiel correspond à plus d’une possibilité, une liste d’achèvements possibles est affichée. Un personnage d’achèvement peut être n’importe quel personnage qui n’est pas utilisé pour les identifiants.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus, voir [Extending the Editor and Language Services](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="implementation-steps"></a>Étapes de mise en œuvre

1. Lorsque l’utilisateur sélectionne **Le mot complet** dans le menu **IntelliSense,** la <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande est envoyée au service linguistique.

2. La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe attrape la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> commande et appelle la <xref:Microsoft.VisualStudio.Package.ParseReason>méthode avec la raison d’analyse de .

3. La <xref:Microsoft.VisualStudio.Package.Source> classe appelle <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> alors la méthode pour obtenir la liste des achèvements de <xref:Microsoft.VisualStudio.Package.CompletionSet> mots possibles, puis affiche les mots dans une liste de conseils d’outil en utilisant la classe.

    S’il n’y a <xref:Microsoft.VisualStudio.Package.Source> qu’un seul mot correspondant, la classe complète le mot.

   Alternativement, si le scanner <xref:Microsoft.VisualStudio.Package.TokenTriggers> retourne la valeur de déclenchement lorsque <xref:Microsoft.VisualStudio.Package.Source> le premier caractère d’un identifiant est tapé, la classe détecte cela et appelle la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode avec la raison d’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Dans ce cas, le parseur doit détecter la présence d’un personnage de sélection des membres et fournir une liste de membres.

## <a name="enabling-support-for-the-complete-word"></a>Permettre le soutien au mot complet
 Pour permettre le support `CodeSense` pour l’achèvement <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> des mots définir le paramètre nommé passé à l’attribut utilisateur associé à l’ensemble de langue. Cela place <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propriété sur la classe.

 Votre analyseur doit retourner une liste de déclarations en <xref:Microsoft.VisualStudio.Package.ParseReason>réponse à la valeur de raison d’analyse, pour l’achèvement des mots d’exploitation.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Mise en œuvre du mot complet dans la méthode ParseSource
 Pour l’achèvement <xref:Microsoft.VisualStudio.Package.Source> des <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> mots, <xref:Microsoft.VisualStudio.Package.AuthoringScope> la classe appelle la méthode sur la classe pour obtenir une liste de correspondances de mots possibles. Vous devez implémenter la liste <xref:Microsoft.VisualStudio.Package.Declarations> dans une classe dérivée de la classe. Consultez <xref:Microsoft.VisualStudio.Package.Declarations> le cours pour plus de détails sur les méthodes que vous devez mettre en œuvre.

 Si la liste ne contient qu’un seul mot, la <xref:Microsoft.VisualStudio.Package.Source> classe insère automatiquement ce mot à la place du mot partiel. Si la liste contient plus <xref:Microsoft.VisualStudio.Package.Source> d’un mot, la classe présente une liste d’outils à partir de laquelle l’utilisateur peut choisir le choix approprié.

 Regardez également l’exemple <xref:Microsoft.VisualStudio.Package.Declarations> d’une mise en œuvre de classe dans [l’achèvement des membres dans un service de langue héritée](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).

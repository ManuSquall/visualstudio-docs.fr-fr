---
title: Saisie semi-automatique de mots dans un Service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f89027e69c319c74e9c61ceb053edd9c2428548d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040802"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Saisie semi-automatique de mot dans un service de langage hérité
Saisie semi-automatique de mot renseigne les caractères manquants sur un mot partiel tapé. En l’absence d’achèvement possible qu’un seul, le mot est terminé lorsque le caractère de saisie semi-automatique est entré. Si le mot partiel correspond à plusieurs possibilités, une liste des saisies semi-automatiques possibles s’affiche. Un caractère de fin peut être n’importe quel caractère qui n’est pas utilisé pour les identificateurs.  
  
 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [extension de l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="implementation-steps"></a>Étapes d’implémentation  
  
1. Lorsque l’utilisateur sélectionne **compléter le mot** à partir de la **IntelliSense** menu, le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande est envoyée au service de langage.  
  
2. Le <xref:Microsoft.VisualStudio.Package.ViewFilter> classe intercepte la commande et appelle le <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3. Le <xref:Microsoft.VisualStudio.Package.Source> classe puis appelle le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode pour obtenir la liste de saisies semi-automatiques possibles word puis affiche les mots dans une info-bulle de liste à l’aide de la <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
    S’il n'existe qu’un seul mot correspondant, le <xref:Microsoft.VisualStudio.Package.Source> classe termine le mot.  
  
   Ou bien, si l’analyseur renvoie la valeur du déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> quand le premier caractère d’un identificateur est tapé, la <xref:Microsoft.VisualStudio.Package.Source> classe le détecte et appelle le <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Dans ce cas, l’analyseur doit détecter la présence d’un caractère de sélection de membre et fournir une liste de membres.  
  
## <a name="enabling-support-for-the-complete-word"></a>L’activation de la prise en charge pour la compléter le mot  
 Pour activer la prise en charge pour le jeu de saisies semi-automatiques word le `CodeSense` nommé paramètre passé à la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> un attribut utilisateur associé au package de langage. Cela définit le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriété sur le <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Votre analyseur doit retourner une liste des déclarations en réponse à la valeur de motif analyse <xref:Microsoft.VisualStudio.Package.ParseReason>, pour l’exécution de word à fonctionner.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implémentation de compléter le mot dans la méthode ParseSource  
 Pour la saisie semi-automatique de word, le <xref:Microsoft.VisualStudio.Package.Source> classe appelle le <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe pour obtenir une liste des correspondances de word possible. Vous devez implémenter la liste dans une classe dérivée de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. Consultez la <xref:Microsoft.VisualStudio.Package.Declarations> classe pour plus d’informations sur les méthodes que vous devez implémenter.  
  
 Si la liste contient uniquement un terme unique, puis la <xref:Microsoft.VisualStudio.Package.Source> classe insère automatiquement ce mot à la place le mot partiel. Si la liste contient plusieurs mots, la <xref:Microsoft.VisualStudio.Package.Source> classe présente une liste de conseil d’outil à partir de laquelle l’utilisateur peut sélectionner le choix approprié.  
  
 Également examiner l’exemple d’un <xref:Microsoft.VisualStudio.Package.Declarations> implémentation de la classe dans [saisie semi-automatique de membres dans un Service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
---
title: "Fin de mot dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a4ab4bd29c753fc03787fbbadbe106d2d8862b10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="word-completion-in-a-legacy-language-service"></a>Mot, compléter dans un Service de langage hérité
Mot, compléter renseigne les caractères manquants sur un mot partiel tapé. S’il n'existe qu’une seule exécution possible, le mot est terminé lorsque le caractère de fin est entré. Si le mot partiel correspond à plusieurs possibilités, une liste de réalisations possibles s’affiche. Un caractère de terminaison peut être n’importe quel caractère qui n’est pas utilisé pour les identificateurs.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [étendre l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="implementation-steps"></a>Étapes d’implémentation  
  
1.  Lorsque l’utilisateur sélectionne **compléter le mot** à partir de la **IntelliSense** menu, le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande est envoyée au service de langage.  
  
2.  Le <xref:Microsoft.VisualStudio.Package.ViewFilter> classe intercepte la commande et les appels de la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  Le <xref:Microsoft.VisualStudio.Package.Source> classe puis appelle le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode pour obtenir la liste des saisies semi-automatiques de word possibles et puis affiche la liste des mots dans une info-bulle à l’aide de la <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
     S’il n'existe qu’un seul mot correspondant, la <xref:Microsoft.VisualStudio.Package.Source> classe termine le mot.  
  
 Ou bien, si l’analyseur renvoie la valeur de déclenchement <xref:Microsoft.VisualStudio.Package.TokenTriggers> lorsque le premier caractère d’un identificateur est de type, le <xref:Microsoft.VisualStudio.Package.Source> classe le détecte et appelle le <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Dans ce cas, l’analyseur doit détecter la présence d’un caractère de la sélection de membre et fournir une liste de membres.  
  
## <a name="enabling-support-for-the-complete-word"></a>L’activation de la prise en charge pour la compléter le mot  
 Pour activer la prise en charge pour le jeu de saisies semi-automatiques word le `CodeSense` nommé paramètre transmis à la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut associé au package de langue de l’utilisateur. Cela permet de définir la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriété sur la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Votre analyseur doit retourner une liste de déclarations en réponse à la valeur de motif de l’analyse <xref:Microsoft.VisualStudio.Package.ParseReason>, pour l’exécution de word à fonctionner.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implémentation de compléter le mot dans la méthode ParseSource  
 Pour l’exécution de word, le <xref:Microsoft.VisualStudio.Package.Source> classe appelle la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe pour obtenir une liste des correspondances de word possibles. Vous devez implémenter la liste dans une classe dérivée de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. Consultez la <xref:Microsoft.VisualStudio.Package.Declarations> classe pour plus d’informations sur les méthodes que vous devez implémenter.  
  
 Si la liste contient uniquement un mot unique, puis la <xref:Microsoft.VisualStudio.Package.Source> classe insère automatiquement ce mot à la place le mot partiel. Si la liste contient plusieurs mots, la <xref:Microsoft.VisualStudio.Package.Source> classe présente une liste de conseil d’outil à partir de laquelle l’utilisateur peut sélectionner le choix approprié.  
  
 Également consulter l’exemple d’un <xref:Microsoft.VisualStudio.Package.Declarations> implémentation de la classe dans [achèvement de membre dans un Service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
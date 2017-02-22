---
title: "Saisie semi-automatique des mots dans un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services de langage (framework package managé), compléter le mot IntelliSense"
  - "IntelliSense, compléter le mot"
  - "Compléter le mot"
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Saisie semi-automatique des mots dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Semi\-automatique renseigne les caractères manquants sur un mot partiellement tapé. S’il n'existe qu’une seule exécution possible, le mot est terminé lorsque le caractère de fin est entré. Si le mot partiel correspond à plusieurs possibilités, une liste de réalisations possibles s’affiche. Un caractère de terminaison peut être n’importe quel caractère qui n’est pas utilisé pour les identificateurs.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [Extension de l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## Étapes d’implémentation  
  
1.  Lorsque l’utilisateur sélectionne **compléter le mot** à partir de la **IntelliSense** menu, le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande est envoyée au service de langage.  
  
2.  La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe intercepte la commande et les appels de la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  La <xref:Microsoft.VisualStudio.Package.Source> classe puis appelle le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode pour obtenir la liste des saisies semi\-automatiques mots possibles, puis affiche la liste des mots dans une info\-bulle à l’aide de la <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
     S’il en existe qu’un seul mot correspondant, la <xref:Microsoft.VisualStudio.Package.Source> classe termine le mot.  
  
 Ou bien, si l’analyseur retourne la valeur du déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> lorsque le premier caractère d’un identificateur est de type, la <xref:Microsoft.VisualStudio.Package.Source> classe détecte et appelle le <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Dans ce cas, l’analyseur doit détecter la présence d’un caractère de sélection de membre et fournir une liste de membres.  
  
## Prise en charge pour la compléter le mot  
 Pour activer la prise en charge pour le jeu de saisies semi\-automatiques word la `CodeSense` nommé du paramètre transmis à la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut associé au package de langue de l’utilisateur. Cela définit le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriété sur la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Votre analyseur doit retourner une liste de déclarations en réponse à la valeur de motif analyse <xref:Microsoft.VisualStudio.Package.ParseReason>, pour l’achèvement de word fonctionner.  
  
## L’implémentation de compléter le mot dans la méthode ParseSource  
 Achèvement de word, le <xref:Microsoft.VisualStudio.Package.Source> classe appelle le <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe pour obtenir une liste des correspondances de mots possibles. Vous devez implémenter la liste dans une classe dérivée de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. Consultez la <xref:Microsoft.VisualStudio.Package.Declarations> classe pour plus d’informations sur les méthodes que vous devez implémenter.  
  
 Si la liste contient un seul mot, puis la <xref:Microsoft.VisualStudio.Package.Source> classe insère automatiquement ce mot à la place de la partie d’un mot. Si la liste contient plusieurs mots, la <xref:Microsoft.VisualStudio.Package.Source> classe présente une liste de conseil d’outil à partir de laquelle l’utilisateur peut sélectionner le choix approprié.  
  
 Également examiner l’exemple d’un <xref:Microsoft.VisualStudio.Package.Declarations> implémentation de la classe dans [Fin de membre dans un Service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
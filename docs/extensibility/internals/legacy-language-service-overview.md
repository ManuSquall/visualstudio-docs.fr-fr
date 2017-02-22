---
title: "Vue d’ensemble du Service de langage ancien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services de langage (framework package managé), à propos des services de langage"
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Vue d’ensemble du Service de langage ancien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un service de langage fournit la prise en charge d'éditeur qui vous permet d'implémenter certaines fonctionnalités de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Les classes de service de \(MPF\) langage du package fournissent la prise en charge complète des fonctionnalités fréquent\-utilisées et la prise en charge partielle d'autres fonctionnalités.  
  
## Fonctionnalités complètement prises en charge dans le MPF  
 Les classes de service de langage de MPF prennent en charge les fonctionnalités suivantes :  
  
-   La coloration syntaxique  
  
-   Mode Plan  
  
-   Commenter les blocs de code  
  
-   Accolades correspondantes  
  
-   Extraits de code  
  
-   Propriétés de document personnalisées  
  
-   Les informations sur les paramètres Intellisense  
  
-   Info express Intellisense  
  
-   Achèvement de membres Intellisense  
  
-   Achèvement de mot Intellisense  
  
## fonctionnalités partiellement prises en charge dans le MPF  
 Le MPF fournit uniquement la prise en charge partielle des fonctionnalités suivantes.  Cela signifie que vous devez implémenter des méthodes qui sont appelées par le MPF.  
  
-   Remettre en forme le code.  Vous fournissez le code qui implémente la remise en forme.  
  
-   La validation des points d'arrêt en identifiant les étendues valides de code.  Vous fournissez le code qui identifie les étendues de code.  
  
-   La prise en charge de la fenêtre d' **Automatique** de débogueur pour afficher des variables.  Vous fournissez le code qui détermine les éléments à afficher dans la fenêtre.  
  
-   prendre en charge **barre de navigation** pour la navigation rapide entre les types et les membres.  Vous implémentez et retournez une classe d'assistance qui remplit listes dans les zones de liste déroulante de **barre de navigation** .  
  
## Implémentation  
 Vous devez effectuer plusieurs étapes pour implémenter le service de langage lui\-même et les fonctionnalités du service de langage que vous souhaitez prendre en charge pour votre langage.  Ces étapes sont décrites dans les rubriques suivantes :  
  
-   [L’implémentation d’un Service de langage](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [L’inscription d’un Service de langage](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Accolades correspondantes dans un Service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Mode plan dans un Service de langage hérité](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Commentaires de Code dans un Service de langage hérité](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Le reformatage du Code dans un Service de langage hérité](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Propriétés de Document personnalisées dans un Service de langage hérité](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Prise en charge des extraits de Code dans un Service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Prise en charge de la barre de Navigation dans un Service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Saisie semi\-automatique des mots dans un Service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Fin de membre dans un Service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Infos Express dans un Service de langage hérité](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Prise en charge de la fenêtre automatique dans un Service de langage hérité](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Validation des points d’arrêt dans un Service de langage hérité](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## Voir aussi  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Extensibilité du Service de langage ancien](../../extensibility/internals/legacy-language-service-extensibility.md)
---
title: "Features1 du Service de langage ancien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services de langage (framework package managé)"
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Fonctionnalit&#233;s du Service de langage ancien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un service de langage managé \(MPF\) du package peut prendre en charge un ou plusieurs fonctionnalités de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , telles que la mise en surbrillance de la syntaxe, Intellisense, et la validation de point d'arrêt.  Chaque fonctionnalité peut être implémenté indépendant des autres mais tous requiert un analyseur et un scanner à l'exception de la syntaxe qui met en surbrillance, qui requiert un seul scanner.  
  
## Dans cette section  
 [Accolades correspondantes dans un Service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Décrit les éléments requis pour prendre en charge la correspondance de couples de langues, également appelé les accolades correspondantes.  
  
 [Commentaires de Code dans un Service de langage hérité](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Décrit les éléments requis pour prendre en charge les commentaires et supprimer les marques de commentaire de code sélectionné.  
  
 [Propriétés de Document personnalisées dans un Service de langage hérité](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Décrit les éléments requis pour prendre en charge les propriétés de document qui sont incorporées dans un fichier source.  
  
 [Mode plan dans un Service de langage hérité](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Décrit les éléments requis pour prendre en charge le mode Plan via l'implémentation des zones masquées.  
  
 [Le reformatage du Code dans un Service de langage hérité](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Décrit les éléments requis pour prendre en charge la remise en forme le code.  
  
 [Prise en charge des extraits de Code dans un Service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Décrit les éléments requis pour prendre en charge les extraits de code, qui sont des segments de code qui sont insérés et peuvent être modifiés.  
  
 [Informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Décrit les éléments requis pour prendre en charge l'opération d'informations sur les paramètres Intellisense pour afficher une signature de méthode lorsque la méthode est tapée.  
  
 [Infos Express dans un Service de langage hérité](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Décrit les éléments requis pour prendre en charge l'opération info express Intellisense pour afficher les informations d'un identificateur.  
  
 [Fin de membre dans un Service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Décrit les éléments requis pour prendre en charge l'opération membre de saisie semi\-automatique Intellisense pour sélectionner un membre d'un espace de noms d'une liste.  
  
 [Saisie semi\-automatique des mots dans un Service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Décrit les éléments requis pour prendre en charge l'opération complète d'Intellisense Word pour effectuer les mots partiellement typés.  
  
 [Prise en charge de la fenêtre automatique dans un Service de langage hérité](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Décrit ce qu'un service de langage peut effectuer pour prendre en charge la fenêtre d' **Automatique** pendant le débogage.  
  
 [Prise en charge de la barre de Navigation dans un Service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Décrit comment utiliser **barre de navigation** entre le haut de la vue de l'éditeur pour fournir une navigation rapide à tout type ou le membre dans le fichier indiqué dans cette vue.  
  
 [Coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Décrit les éléments requis pour prendre en charge la mise en surbrillance de la syntaxe de code source.  
  
 [Validation des points d’arrêt dans un Service de langage hérité](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Décrit ce qu'un service de langage peut effectuer pour prendre en charge la validation des points d'arrêt en dehors d'un débogueur.  
  
## Rubriques connexes  
 [Scanneur et analyseur du Service de langage ancien](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Décrit l'analyseur et le scanner requis pour implémenter toutes les fonctionnalités d'un service de langage qui utilise managed package.  
  
 [L’implémentation d’un Service de langage](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Décrit les éléments requis pour implémenter un service de langage à l'aide de le MPF.  
  
 [L’inscription d’un Service de langage](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Décrit les étapes requises pour enregistrer un service de langage MPF\-basé avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)  
 Explique comment Intellisense rend les accès aux guides de référence du langage.  
  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fournit des informations sur l'utilisation de managed package \(MPF\) pour implémenter un service de langage complet en code managé.
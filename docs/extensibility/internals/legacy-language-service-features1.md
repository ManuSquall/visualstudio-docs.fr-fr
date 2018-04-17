---
title: Langage hérité Service Features1 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c931147d20454a920e20cec61e1f6000a9b043d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-features"></a>Fonctionnalités de Service de langage hérité
Un service de langage managé package framework (MPF) peut prendre en charge un ou plusieurs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fonctionnalités, telles que la mise en surbrillance de syntaxe, IntelliSense et validation de point d’arrêt. Chaque fonctionnalité peut être implémentée indépendant des autres, mais tous requièrent un analyseur et un analyseur à l’exception de la mise en surbrillance de syntaxe, ce qui nécessite uniquement un scanneur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge de la paire de langue correspondante, également connu sous la correspondance des accolades.  
  
 [Commentaire du code dans un service de langage hérité](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge les commentaires et commentaire du code sélectionné.  
  
 [Propriétés de document personnalisé dans un service de langage hérité](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge les propriétés de document qui sont incorporées dans un fichier source.  
  
 [Mode Plan dans un service de langage hérité](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge le mode plan à l’implémentation des zones masquées.  
  
 [Reformatage du code dans un service de langage hérité](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge le code de reformatage.  
  
 [Prise en charge des extraits de code dans un service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge des extraits de code, qui sont des segments de code qui sont insérées et peuvent être modifiées.  
  
 [Informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Décrit ce qui est requis pour prendre en charge l’opération d’informations sur les paramètres IntelliSense pour l’affichage d’une signature de méthode que la méthode est inséré automatiquement.  
  
 [Informations rapides dans un service de langage hérité](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge l’opération Info express IntelliSense pour afficher des informations sur un identificateur.  
  
 [Saisie semi-automatique de membre dans un service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge l’opération de saisie semi-automatique IntelliSense membre pour la sélection d’un membre d’un espace de noms dans une liste.  
  
 [Saisie semi-automatique de mot dans un service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge l’opération IntelliSense compléter le mot pour terminer les mots partiellement typés.  
  
 [Prise en charge de Fenêtre Automatique dans un service de langage hérité](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Décrit ce que peut faire un service de langage pour prendre en charge la **automatique** fenêtre pendant que vous déboguez.  
  
 [Prise en charge de la barre de navigation dans un service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Décrit comment utiliser le **barre de Navigation** en haut de la vue de l’éditeur pour fournir une navigation rapide à n’importe quel type ou d’un membre dans le fichier indiqué dans cette vue...  
  
 [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge la mise en surbrillance de la syntaxe du code source.  
  
 [Validation des points d’arrêt dans un service de langage hérité](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Décrit ce que peut faire un service de langage pour prendre en charge les points d’arrêt de validation en dehors d’un débogueur.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Décrit l’analyseur et l’analyseur qui sont requis pour implémenter toutes les fonctionnalités d’un service de langage qui utilise managed package framework.  
  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Décrit ce qui est requis pour implémenter un service de langage à l’aide du MPF.  
  
 [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Décrit les étapes requises pour inscrire un service de langage MPF avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)  
 Explique comment IntelliSense rend facile d’accès de référence du langage.  
  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fournit des informations sur l’utilisation de managed package framework (MPF) pour implémenter un service de langage complet dans le code managé.
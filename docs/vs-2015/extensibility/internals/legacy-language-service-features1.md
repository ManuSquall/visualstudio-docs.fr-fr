---
title: Features1 de Service de langage hérité | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ed5b66c8148df36b89cfb6e6ae048a05f393551
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501096"
---
# <a name="legacy-language-service-features"></a>Fonctionnalités de Service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Features1 de Service de langage hérité](https://docs.microsoft.com/visualstudio/extensibility/internals/legacy-language-service-features1).  
  
Un service de langage de framework (MPF) package managé peut prendre en charge un ou plusieurs [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fonctionnalités, telles que la coloration syntaxique, IntelliSense et validation de point d’arrêt. Chaque fonctionnalité peut être implémentée indépendant des autres, mais requièrent tous un analyseur et un analyseur à l’exception de la coloration syntaxique, ce qui nécessite uniquement un scanneur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Décrit ce qui est nécessaire pour prendre en charge de langage appariement, également appelé correspondance des accolades.  
  
 [Commentaire du code dans un service de langage hérité](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Décrit ce qui est nécessaire pour prendre en charge les commentaires et supprimant des commentaires de code sélectionné.  
  
 [Propriétés de document personnalisé dans un service de langage hérité](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Décrit ce qui est nécessaire pour prendre en charge les propriétés de document qui sont incorporées dans un fichier source.  
  
 [Mode Plan dans un service de langage hérité](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Décrit ce qui est nécessaire pour prendre en charge le mode plan via l’implémentation de zones masquées.  
  
 [Reformatage du code dans un service de langage hérité](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Décrit ce qui est nécessaire pour prendre en charge le reformatage de code.  
  
 [Prise en charge des extraits de code dans un service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Décrit ce qui est nécessaire pour prendre en charge des extraits de code, qui sont des segments de code qui sont insérés et peuvent être modifiées.  
  
 [Informations sur les paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Décrit ce qui est nécessaire pour prendre en charge l’opération d’informations sur les paramètres IntelliSense pour l’affichage d’une signature de méthode comme la méthode est de type.  
  
 [Informations rapides dans un service de langage hérité](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Décrit ce qui est nécessaire pour prendre en charge l’opération d’Info express IntelliSense pour afficher des informations sur un identificateur.  
  
 [Saisie semi-automatique de membre dans un service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Décrit ce qui est requis pour prendre en charge l’opération de saisie semi-automatique de membres IntelliSense pour la sélection d’un membre d’un espace de noms à partir d’une liste.  
  
 [Saisie semi-automatique de mot dans un service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Décrit ce qui est nécessaire pour prendre en charge l’opération IntelliSense compléter le mot pour terminer les mots partiellement typés.  
  
 [Prise en charge de Fenêtre Automatique dans un service de langage hérité](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Décrit ce que peut faire un service de langage pour prendre en charge la **automatique** fenêtre pendant le débogage.  
  
 [Prise en charge de la barre de navigation dans un service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Décrit comment utiliser le **barre de Navigation** dans la partie supérieure de l’affichage de l’éditeur pour fournir une navigation rapide à n’importe quel type ou un membre dans le fichier indiqué dans cette vue...  
  
 [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Décrit ce qui est nécessaire pour prendre en charge la coloration syntaxique du code source.  
  
 [Validation des points d’arrêt dans un service de langage hérité](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Décrit ce que peut faire un service de langage pour prendre en charge des points d’arrêt lors de la validation en dehors d’un débogueur.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Décrit l’analyseur et l’analyseur qui sont requis pour implémenter toutes les fonctionnalités d’un service de langage qui utilise l’infrastructure de package gérée.  
  
 [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Décrit ce qui est nécessaire pour implémenter un service de langage à l’aide du MPF.  
  
 [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Décrit les étapes qui sont requises pour l’inscription à un service de langage MPF [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)  
 Explique comment IntelliSense rend facile d’accéder aux références du langage.  
  
 [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fournit des informations sur l’utilisation de l’infrastructure de package managé (MPF) pour implémenter un service de langage complet dans le code managé.


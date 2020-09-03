---
title: Vue d’ensemble du service de langage hérité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5964aa82d76791d29313ac787f1216c9c9ad283
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202713"
---
# <a name="legacy-language-service-overview"></a>Présentation du service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un service de langage fournit une prise en charge de l’éditeur qui vous permet d’implémenter certaines [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fonctionnalités. Les classes du service de langage de l’infrastructure de package managé (MPF) fournissent une prise en charge complète des fonctionnalités fréquemment utilisées et de la prise en charge partielle des autres fonctionnalités.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Fonctionnalités entièrement prises en charge dans le MPF  
 Les classes du service de langage MPF prennent en charge les fonctionnalités suivantes :  
  
- Mise en surbrillance de la syntaxe  
  
- mode Plan  
  
- Commenter des blocs de code  
  
- Correspondance d’accolade  
  
- Extraits de code  
  
- Propriétés de document personnalisées  
  
- Informations sur les paramètres IntelliSense  
  
- Info Express IntelliSense  
  
- Saisie semi-automatique des membres IntelliSense  
  
- Saisie semi-automatique des mots IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Fonctionnalités partiellement prises en charge dans le MPF  
 Le MPF fournit uniquement une prise en charge partielle des fonctionnalités suivantes. Cela signifie que vous devez implémenter les méthodes qui sont appelées par le MPF.  
  
- Reformatage du code. Vous fournissez le code qui implémente le reformatage.  
  
- Validation des points d’arrêt en identifiant les étendues de code valides. Vous fournissez le code qui identifie les étendues de code.  
  
- Prise en charge de la fenêtre **automatique** du débogueur pour afficher les variables. Vous fournissez le code qui détermine les éléments à afficher dans la fenêtre.  
  
- Prise en charge de la **barre de navigation** pour la navigation rapide entre les types et les membres. Vous implémentez et retournez une classe d’assistance qui remplit les listes dans les zones de liste déroulante de la **barre de navigation** .  
  
## <a name="implementation"></a>Implémentation  
 Vous devez effectuer plusieurs étapes pour implémenter le service de langage lui-même et les fonctionnalités du service de langage que vous souhaitez prendre en charge pour votre langue. Ces étapes sont décrites dans les rubriques suivantes :  
  
- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
- [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
- [Mode Plan dans un service de langage hérité](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
- [Commentaire du code dans un service de langage hérité](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
- [Reformatage du code dans un service de langage hérité](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
- [Propriétés de document personnalisé dans un service de langage hérité](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
- [Prise en charge des extraits de code dans un service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
- [Prise en charge de la barre de navigation dans un service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
- [Saisie semi-automatique de mot dans un service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
- [Saisie semi-automatique de membre dans un service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
- [Informations sur les paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
- [Informations rapides dans un service de langage hérité](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
- [Prise en charge de Fenêtre Automatique dans un service de langage hérité](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
- [Validation des points d’arrêt dans un service de langage hérité](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Extensibilité du service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md)

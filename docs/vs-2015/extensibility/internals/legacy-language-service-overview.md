---
title: Vue d’ensemble du Service de langage hérité | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6f5a060776126756b104b7f24c7b216ac881d1b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302703"
---
# <a name="legacy-language-service-overview"></a>Présentation du service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un service de langage prend en charge de l’éditeur qui vous permet d’implémenter certains [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fonctionnalités. Les classes de service de langage de Managed Package Framework (MPF) totalement en charge pour les fonctionnalités les plus courantes et la prise en charge partielle d’autres fonctionnalités.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Fonctionnalités entièrement prises en charge dans le MPF  
 Les classes de service de langage MPF prennent en charge les fonctionnalités suivantes :  
  
-   Mise en surbrillance de la syntaxe  
  
-   mode Plan  
  
-   Commentaires des blocs de code  
  
-   Accolades correspondantes  
  
-   Extraits de code  
  
-   Propriétés de document personnalisées  
  
-   Informations sur les paramètres IntelliSense  
  
-   IntelliSense Info express  
  
-   Saisie semi-automatique de membres IntelliSense  
  
-   Saisie semi-automatique IntelliSense word  
  
## <a name="partially-supported-features-in-the-mpf"></a>Fonctionnalités partiellement prises en charge dans le MPF  
 MPF fournit la prise en charge partielle uniquement pour les fonctionnalités suivantes. Cela signifie que vous devez implémenter les méthodes qui sont appelées par du MPF.  
  
-   Reformatage du code. Vous fournissez le code qui implémente la remise en forme.  
  
-   Points d’arrêt lors de la validation en identifiant les étendues de code valide. Vous fournissez le code qui identifie les étendues de code.  
  
-   Prise en charge du débogueur **automatique** fenêtre pour l’affichage des variables. Vous fournissez le code qui détermine les éléments à afficher dans la fenêtre.  
  
-   Prise en charge la **barre de Navigation** pour la navigation rapide entre les types et membres. Vous implémentez et retourner une classe d’assistance qui remplit les listes dans le **barre de Navigation** zones de liste déroulante.  
  
## <a name="implementation"></a>Implémentation  
 Vous devez effectuer plusieurs étapes pour implémenter le service de langage lui-même et les fonctionnalités de service de langage que vous souhaitez prendre en charge pour votre langue. Ces étapes sont décrites dans les rubriques suivantes :  
  
-   [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Mode Plan dans un service de langage hérité](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Commentaire du code dans un service de langage hérité](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Reformatage du code dans un service de langage hérité](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Propriétés de document personnalisé dans un service de langage hérité](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Prise en charge des extraits de code dans un service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Prise en charge de la barre de navigation dans un service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Saisie semi-automatique de mot dans un service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Saisie semi-automatique de membre dans un service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Informations sur les paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Informations rapides dans un service de langage hérité](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Prise en charge de Fenêtre Automatique dans un service de langage hérité](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Validation des points d’arrêt dans un service de langage hérité](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Extensibilité du service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md)


---
title: "L’impl&#233;mentation d’un Service1 de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services de langage gérés"
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Impl&#233;mentation d’un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser les classes dans l’infrastructure du package managé \(MPF\) pour implémenter un service de langage ancien qui prend en charge un large éventail de fonctionnalités, telles que la mise en surbrillance de la syntaxe de la correspondance des accolades et la saisie semi\-automatique IntelliSense.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [Éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## Dans cette section  
 [Vue d’ensemble du Service de langage ancien](../../extensibility/internals/legacy-language-service-overview.md)  
 Vue d’ensemble des fonctionnalités du service de langage qui prennent en charge les MPF.  
  
 [L’implémentation d’un Service de langage](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Décrit ce qui est nécessaire pour implémenter un service de langage à l’aide du chargeur multifonctions.  
  
 [L’inscription d’un Service de langage](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Décrit les étapes qui sont requises pour l’inscription à un service de langage MPF [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Scanneur et analyseur du Service de langage ancien](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Décrit les deux analyseurs qui sont requises pour implémenter toutes les fonctionnalités d’un service de langage à l’aide du chargeur multifonctions.  
  
 [Procédure pas à pas : Création d’un Service de langage hérité](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Fournit les étapes de base qui sont requises pour implémenter un service de langage MPF dans un VSPackage.  
  
 [Procédure pas à pas : Obtention d’une liste d’extraits de Code installé \(implémentation hérité\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Présente les techniques de récupération d’une liste d’extraits de code installé.  
  
 [Fonctionnalités du Service de langage ancien](../../extensibility/internals/legacy-language-service-features1.md)  
 Fournit des liens vers des rubriques détaillant ce qui doit être fait pour implémenter toutes les fonctionnalités d’un service de langage à l’aide du chargeur multifonctions.
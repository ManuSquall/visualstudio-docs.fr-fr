---
title: "Extensibilit&#233; du Service de langage ancien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services de langage"
  - "Visual Studio, les services de langage"
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 42
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 42
---
# Extensibilit&#233; du Service de langage ancien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un service de langage prend en charge de spécifique à la langue d’édition du code source dans l’IDE.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [Éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
 Cette section décrit la structure et l’implémentation d’un service de langage ancien.  
  
## Dans cette section  
 [Migration d’un Service de langage hérité](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Explique comment mettre à jour un service de langage de Visual Studio 2008 vers la dernière version.  
  
 [Fondamentaux du Service de langage ancien](../../extensibility/internals/legacy-language-service-essentials.md)  
 Fournit des informations sur le développement des services de langage pour intégrer un langage de programmation dans Visual Studio.  
  
 [Développement d'un Service de langage](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Fournit des liens vers des rubriques qui peuvent vous aider à créer un service de langage.  
  
 [Couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Fournit des informations sur la prise en charge de la mise en évidence dans un service de langage.  
  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fournit des informations sur l’utilisation de l’infrastructure du package managé \(MPF\) pour implémenter un service de langage complet dans le code managé.  
  
 [Prise en charge d'outils de consultation du symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Décrit les outils et bibliothèques qui vous permettent de parcourir les vues de l’arborescence de symboles dans l’IDE.  
  
## Rubriques connexes  
 [Éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md)  
 Fournit une vue d’ensemble des éditeurs de Visual Studio.  
  
 [Prise en charge du Service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md)  
 Fournit des informations et un lien vers le SDK Visual Studio de débogage, qui contient les informations requises pour créer et personnaliser les composants du débogueur permet de déboguer des programmes.
---
title: Extensibilité de Service de langage hérité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb7d8165060fa3b9a6445ad71a977c79414056f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-extensibility"></a>Extensibilité de Service de langage hérité
Un service de langage fournit la prise en charge linguistiques pour modifier le code source dans l’IDE.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
 Cette section décrit la structure et l’implémentation d’un service de langage hérité.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Migration d’un service de langage hérité](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Explique comment mettre à jour un service de langage de Visual Studio 2008 vers la dernière version.  
  
 [Éléments fondamentaux du service de langage hérité](../../extensibility/internals/legacy-language-service-essentials.md)  
 Fournit des informations importantes sur la façon de développer des services de langage pour intégrer un langage de programmation Visual Studio.  
  
 [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Fournit des liens vers des rubriques qui peuvent vous aider à créer un service de langage.  
  
 [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Fournit des informations sur la prise en charge de la syntaxe de la mise en surbrillance dans un service de langage.  
  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fournit des informations sur l’utilisation de managed package framework (MPF) pour implémenter un service de langage complet dans le code managé.  
  
 [Prise en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Décrit les bibliothèques et des outils qui vous permettent de parcourir les vues de l’arborescence de symboles dans l’IDE.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Extensions de l’éditeur et du service de langage](../../extensibility/editor-and-language-service-extensions.md)  
 Fournit une vue d’ensemble des éditeurs de Visual Studio.  
  
 [Prise en charge du service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md)  
 Fournit des informations et un lien vers le SDK Visual Studio de débogage, qui contient les informations requises pour créer et personnaliser les composants du débogueur permet de déboguer des programmes.
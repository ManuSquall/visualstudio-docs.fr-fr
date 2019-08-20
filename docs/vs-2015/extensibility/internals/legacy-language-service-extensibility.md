---
title: Extensibilité du Service de langage hérité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9346311aac4bc5833005423e90c2eb92faddcb84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194983"
---
# <a name="legacy-language-service-extensibility"></a>Extensibilité du service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un service de langage prend en charge de spécifique à la langue d’édition du code source dans l’IDE.  
  
 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
 Cette section décrit la structure et l’implémentation d’un service de langage hérité.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Migration d’un service de langage hérité](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Explique comment mettre à jour un service de langage à partir de Visual Studio 2008 vers la dernière version.  
  
 [Éléments fondamentaux du service de langage hérité](../../extensibility/internals/legacy-language-service-essentials.md)  
 Fournit des informations importantes sur le développement des services de langage pour intégrer un langage de programmation dans Visual Studio.  
  
 [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Fournit des liens vers des rubriques qui peuvent vous aider à créer un service de langage.  
  
 [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Fournit des informations sur la prise en charge la coloration syntaxique dans un service de langage.  
  
 [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fournit des informations sur l’utilisation de l’infrastructure de package managé (MPF) pour implémenter un service de langage complet dans le code managé.  
  
 [Prise en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Décrit les bibliothèques et des outils qui vous permettent de parcourir les vues de l’arborescence de symboles dans l’IDE.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Extensions de l’éditeur et du service de langage](../../extensibility/editor-and-language-service-extensions.md)  
 Fournit une vue d’ensemble des éditeurs de Visual Studio.  
  
 [Prise en charge du service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md)  
 Fournit des informations et un lien vers le SDK Visual Studio de débogage, qui contient les informations requises pour créer et personnaliser les composants du débogueur permet de déboguer des programmes.

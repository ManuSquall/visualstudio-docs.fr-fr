---
title: "Implémentation d’un Service1 de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 304d99c1ddd5fdfddba0c4df88fc4eeeb9dcb7ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-a-legacy-language-service"></a>Implémentation d’un Service de langage hérité
Vous pouvez utiliser les classes de managed package framework (MPF) pour implémenter un service de langage hérité qui prend en charge un large éventail de fonctionnalités, telles que mise en surbrillance de la syntaxe, la correspondance d’accolade et la saisie semi-automatique IntelliSense.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Présentation du service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)  
 Vue d’ensemble des fonctionnalités du service de langage pris en charge dans le MPF.  
  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Décrit ce qui est requis pour implémenter un service de langage à l’aide de MPF.  
  
 [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Décrit les étapes requises pour inscrire un service de langage MPF avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Décrit les deux analyseurs qui sont requis pour implémenter toutes les fonctionnalités d’un service de langage à l’aide du MPF.  
  
 [Procédure pas à pas : Création d’un service de langage hérité](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Fournit les étapes de base qui sont requis pour implémenter un service de langage MPF dans un VSPackage.  
  
 [Procédure pas à pas : Obtention d’une liste d’extraits de code installés (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Présente les techniques de récupération d’une liste des extraits de code installé.  
  
 [Fonctionnalités de Service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)  
 Fournit des liens vers des rubriques détaillant ce qui doit être fait pour implémenter toutes les fonctionnalités d’un service de langage à l’aide de MPF.
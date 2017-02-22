---
title: "D&#233;veloppement d’un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.vsip.LangServWiz.langtoks"
  - "vs.vsip.LangServWiz.welcome"
  - "vs.vsip.LangServWiz.langSpec"
  - "vs.vsip.LangServWiz.langInfo"
  - "vs.vsip.LangServWiz.langServOpts"
helpviewer_keywords: 
  - "services de langage de développement"
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# D&#233;veloppement d&#39;un Service de langage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette section fournit des liens vers des rubriques qui vous aident à créer un service de langage hérité.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [Éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## Dans cette section  
 [Modèle d’un Service de langage hérité](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Fournit un modèle d’un service de langage minimal pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éditeur principal. Vous pouvez utiliser ce modèle comme guide pour créer votre propre service de langage.  
  
 [Interfaces de Service de langage ancien](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Décrit les objets requis pour implémenter un service de langage et fournit une liste d’objets supplémentaires que vous pouvez utiliser pour fournir la mise en surbrillance de la syntaxe, les données de la méthode et autres fonctionnalités.  
  
 [Interception des commandes de Service de langage hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Décrit comment insérer un filtre de commande dans votre service de langage pour intercepter les commandes qui prendrait autrement en charge l’affichage de texte.  
  
 [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Fournit des informations sur l’inscription de votre service de langage à l’aide de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Prise en charge du Service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md)  
 Décrit comment un service de langage peut fournir des fonctionnalités pour prendre en charge d’un débogueur.  
  
 [Liste de vérification : Création d’un Service de langage hérité](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Fournit des instructions détaillées pour la création et l’intégration d’un service de langage pour l’éditeur principal.  
  
## Rubriques connexes  
 [Couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Explique comment implémenter la mise en surbrillance de syntaxe dans votre service de langage.  
  
 [Saisie semi\-automatique des instructions dans un Service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Décrit la saisie semi\-automatique des instructions, le processus par lequel un service de langage permet aux utilisateurs de terminer un élément qui ils ont commencé à taper ou le mot clé de langage.  
  
 [Informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Décrit comment fournir des conseils de méthode pour les méthodes et les fonctions surchargées.  
  
 [Comment : fournir la prise en charge du texte masqué dans un Service de langage hérité](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Explique l’objectif d’une zone de texte masqué et fournit des instructions sur l’implémentation d’une zone de texte masquée.  
  
 [Comment : fournir une prise en charge étendue de plan dans un Service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Explique les deux options qui prennent en charge en mode plan pour votre langage de prendre en charge les *réduire aux définitions* commande.
---
title: Développement d’un Service de langage hérité | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 253bd334abd15fc19b1937c7c2c096ba026ad882
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172144"
---
# <a name="developing-a-legacy-language-service"></a>Développement d’un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette section fournit des liens vers des rubriques qui vous aident à créer un service de langage hérité.  
  
 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modèle d’un service de langage hérité](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Fournit un modèle d’un service de langage minimal pour le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] éditeur principal. Vous pouvez utiliser ce modèle comme guide pour créer votre propre service de langage.  
  
 [Interfaces du service de langage hérité](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Décrit les objets requis pour implémenter un service de langage et fournit une liste d’objets supplémentaires que vous pouvez utiliser pour fournir la coloration syntaxique, les données de méthode et d’autres fonctionnalités.  
  
 [Interception des commandes du service de langage hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Décrit comment insérer un filtre de commande dans votre service de langage pour les commandes intercept qui prendrait autrement en charge l’affichage de texte.  
  
 [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Fournit des informations sur l’inscription de votre service de langage à l’aide de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Prise en charge du service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md)  
 Décrit comment un service de langage peut fournir des fonctionnalités pour prendre en charge d’un débogueur.  
  
 [Liste de vérification : création d’un service de langage hérité](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Fournit des instructions détaillées pour la création et l’intégration d’un service de langage pour l’éditeur principal.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Explique comment implémenter la coloration syntaxique dans votre service de langage.  
  
 [Saisie semi-automatique des instructions dans un service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Décrit la saisie semi-automatique des instructions, le processus par lequel un service de langage aide les utilisateurs à terminer un mot clé de langage ou l’élément qu’il démarre en tapant.  
  
 [Informations sur les paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Décrit comment fournir des conseils de méthode pour les méthodes et les fonctions surchargées.  
  
 [Guide pratique pour fournir la prise en charge de texte masqué dans un service de langage hérité](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Explique l’objectif d’une zone de texte masqué et fournit des instructions sur la façon d’implémenter une zone de texte masqué.  
  
 [Guide pratique pour fournir la prise en charge étendue du Mode Plan dans un service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Explique les deux options qui prennent en charge en mode plan pour votre langage au-delà de la prise en charge la *réduire aux définitions* commande.


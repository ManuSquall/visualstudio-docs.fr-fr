---
title: Développer un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708671"
---
# <a name="develop-a-legacy-language-service"></a>Développer un service linguistique hérité
Cette section est reliée à des sujets qui vous aident à créer un service linguistique hérité.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon de mettre en œuvre un service linguistique, consultez [les extensions de service d’éditeur et de langue](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="in-this-section"></a>Contenu de cette section
- [Modèle d’un service linguistique hérité](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Fournit un modèle d’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] service linguistique minimal pour l’éditeur de base. Vous pouvez utiliser ce modèle comme guide pour créer votre propre service linguistique.

- [Interfaces de service linguistique héritées](../../extensibility/internals/legacy-language-service-interfaces.md)

 Discute des objets nécessaires à la mise en œuvre d’un service linguistique et fournit une liste d’objets supplémentaires que vous pouvez utiliser pour fournir la mise en évidence de la syntaxe, les données de méthode, et d’autres fonctionnalités.

- [Intercepter les commandes de service linguistique hérité](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Décrit comment insérer un filtre de commande dans votre service linguistique pour intercepter les commandes que la vue de texte gérerait autrement.

- [Enregistrer un service linguistique hérité](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Fournit des informations sur la façon [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]d’enregistrer votre service linguistique en utilisant .

- [Soutien au service linguistique pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md)

 Décrit comment un service linguistique peut fournir des fonctionnalités pour soutenir un débbugger.

- [Liste de contrôle : Créer un service linguistique hérité](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Fournit des instructions étape par étape pour la création et l’intégration d’un service linguistique pour l’éditeur de base.

## <a name="related-sections"></a>Sections connexes
- [Coloriage Syntax dans un service linguistique hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Discute de la façon d’implémenter la mise en évidence de la syntaxe dans votre service linguistique.

- [Achèvement de l’énoncé dans un service linguistique hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Discute de l’achèvement des relevés, le processus par lequel un service linguistique aide les utilisateurs à terminer un mot clé ou un élément de langue qu’ils ont commencé à taper.

- [Informations sur les paramètres dans un service linguistique hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Décrit comment fournir des conseils de méthode pour les fonctions et les méthodes surchargées.

- [Comment : Fournir un support texte caché dans un service linguistique hérité](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Explique le but d’une région de texte caché et fournit des instructions sur la façon de mettre en œuvre une région de texte caché.

- [Comment : Fournir un soutien élargi dans un service linguistique hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explique les deux options qui étendent le soutien à votre langue au-delà de l’appui de la commande *Collapse to Definitions.*

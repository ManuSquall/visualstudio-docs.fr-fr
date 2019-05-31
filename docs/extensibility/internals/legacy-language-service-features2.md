---
title: 'Suivantes : 2 du Service de langage hérité | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de7e0fa6a229929a34ed3654c3a4e03e02d1129b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333502"
---
# <a name="legacy-language-service-features"></a>Fonctionnalités de Service de langage hérité
Les rubriques suivantes répertorient certaines des fonctionnalités du service de langage hérité que vous pouvez fournir.

 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="in-this-section"></a>Dans cette section
- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Explique comment implémenter la coloration syntaxique.

- [Mise en forme automatique dans un service de langage hérité](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Explique comment implémenter la mise en forme automatique.

- [Informations sur les paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Explique comment implémenter l’info-bulle des informations de paramètre IntelliSense.

- [Saisie semi-automatique des instructions dans un service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Explique comment implémenter la liste d’instructions IntelliSense et la liste de saisie semi-automatique de membre.

- [Mode Plan et texte masqué dans un service de langage hérité](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Explique comment implémenter le texte masqué ou en mode plan.

- [Guide pratique pour fournir la prise en charge étendue du mode Plan dans un service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explique certaines des étapes de l’implémentation de prise en charge du débogueur...

## <a name="related-sections"></a>Rubriques connexes
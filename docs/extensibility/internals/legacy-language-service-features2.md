---
title: Service de langage hérité Features2 | Microsoft Docs
description: Découvrez quelques-unes des fonctionnalités du service de langage hérité que vous pouvez fournir à l’aide des extensions Managed Extensibility Framework (MEF) dans le kit de développement logiciel (SDK) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a12ee207f7fb7e4f4e2d202d5d63d468e9cea547
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074481"
---
# <a name="legacy-language-service-features-2"></a>Fonctionnalités du service de langage hérité 2
Les rubriques suivantes répertorient certaines des fonctionnalités du service de langage hérité que vous pouvez fournir.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et extensions du service de langage](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="in-this-section"></a>Dans cette section
- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Explique comment implémenter la coloration de la syntaxe.

- [Mise en forme automatique dans un service de langage hérité](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Explique comment implémenter la mise en forme automatique.

- [Informations sur les paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Explique comment implémenter l’info-bulle informations sur les paramètres IntelliSense.

- [Saisie semi-automatique des instructions dans un service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Explique comment implémenter la liste des instructions IntelliSense et la liste de saisie semi-automatique des membres.

- [Mode Plan et texte masqué dans un service de langage hérité](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Explique comment implémenter le mode plan ou le texte masqué.

- [Guide pratique pour fournir la prise en charge étendue du Mode Plan dans un service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explique certaines étapes de l’implémentation de la prise en charge du débogueur.

## <a name="related-sections"></a>Sections connexes

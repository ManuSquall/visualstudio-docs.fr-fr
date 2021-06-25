---
title: Implémentation d’un Service1 de langage hérité | Microsoft Docs
description: Découvrez comment implémenter un service de langage hérité qui prend en charge les fonctionnalités du service de langage étendu, à l’aide de Managed package Framework (MPF). Partie 1 sur 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 34be4e54fbce413fe5ba916892216a9234d4ba93
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901147"
---
# <a name="implementing-a-legacy-language-service-1"></a>Implémentation d’un service de langage hérité 1
Vous pouvez utiliser des classes dans Managed package Framework (MPF) pour implémenter un service de langage hérité qui prend en charge un large éventail de fonctionnalités, telles que la mise en surbrillance de la syntaxe, la correspondance des accolades et la saisie semi-automatique IntelliSense.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et extensions du service de langage](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="in-this-section"></a>Dans cette section
- [Présentation du service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)

 Vue d’ensemble des fonctionnalités du service de langage prises en charge dans MPF.

- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Décrit ce qui est requis pour implémenter un service de langage à l’aide de MPF.

- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Décrit les étapes nécessaires pour inscrire un service de langage basé sur MPF avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Décrit les deux analyseurs nécessaires pour implémenter toutes les fonctionnalités d’un service de langage à l’aide du MPF.

- [Procédure pas à pas : création d’un service de langage hérité](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Fournit les étapes de base nécessaires pour implémenter un service de langage MPF dans un VSPackage.

- [Procédure pas à pas : obtention d’une liste d’extraits de code installés (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Montre les techniques de récupération d’une liste d’extraits de code installés.

- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)

 Fournit des liens vers des rubriques qui décrivent en détail ce qui doit être fait pour implémenter toutes les fonctionnalités d’un service de langage à l’aide de MPF.

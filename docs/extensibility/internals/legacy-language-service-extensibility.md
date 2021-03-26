---
title: Extensibilité du service de langage hérité | Microsoft Docs
description: En savoir plus sur la structure, l’implémentation et l’extensibilité des services de langage hérités dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f22d6997d932884e5aeb8d794b7884b40a8d5dab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074494"
---
# <a name="legacy-language-service-extensibility"></a>Extensibilité du service de langage hérité
Un service de langage fournit une prise en charge spécifique à la langue pour la modification du code source dans l’IDE.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et extensions du service de langage](../../extensibility/editor-and-language-service-extensions.md).

 Cette section décrit la structure et l’implémentation d’un service de langage hérité.

## <a name="in-this-section"></a>Dans cette section
- [Migration d’un service de langage hérité](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Explique comment mettre à jour un service de langage de Visual Studio 2008 vers la version la plus récente.

- [Éléments fondamentaux du service de langage hérité](../../extensibility/internals/legacy-language-service-essentials.md)

 Fournit des informations importantes sur le développement de services de langage pour intégrer un langage de programmation dans Visual Studio.

- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)

 Fournit des liens vers des rubriques qui peuvent vous aider à créer un service de langage.

- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Fournit des informations sur la prise en charge de la mise en surbrillance syntaxique dans un service de langage.

- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Fournit des informations sur l’utilisation de Managed package Framework (MPF) pour implémenter un service de langage complet dans du code managé.

- [Prise en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Décrit les bibliothèques et les outils qui vous permettent de parcourir les arborescences de symboles dans l’IDE.

## <a name="related-sections"></a>Sections connexes
- [Extensions de l’éditeur et du service de langage](../../extensibility/editor-and-language-service-extensions.md)

 Fournit une vue d’ensemble des éditeurs Visual Studio.

- [Prise en charge du service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md)

 Fournit des informations sur et un lien vers le kit de développement logiciel (SDK) de débogage Visual Studio, qui contient les informations requises pour créer et personnaliser les composants du débogueur utilisés pour déboguer des programmes.

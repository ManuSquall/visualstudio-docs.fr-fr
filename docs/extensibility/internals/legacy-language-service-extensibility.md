---
title: Legacy Language Service Extensibility (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b5ec3de8d7b0b9466e162c3ee193c130634cd4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707405"
---
# <a name="legacy-language-service-extensibility"></a>Extensibilité du service de langage hérité
Un service linguistique fournit un support spécifique à la langue pour l’édition du code source dans l’IDE.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon de mettre en œuvre un service linguistique, consultez [Editor et Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

 Cette section traite de la structure et de la mise en œuvre d’un service linguistique hérité.

## <a name="in-this-section"></a>Dans cette section
- [Migration d’un service de langage hérité](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Explique comment mettre à jour un service linguistique de Visual Studio 2008 à la dernière version.

- [Éléments fondamentaux du service de langage hérité](../../extensibility/internals/legacy-language-service-essentials.md)

 Fournit des informations importantes sur la façon de développer des services linguistiques pour intégrer un langage de programmation dans Visual Studio.

- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)

 Fournit des liens vers des sujets qui peuvent vous aider à créer un service linguistique.

- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Fournit des informations sur la mise en évidence de la syntaxe à l’appui dans un service linguistique.

- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Fournit des informations sur la façon d’utiliser le cadre de forfait géré (MPF) pour mettre en œuvre un service linguistique complet dans le code géré.

- [Prise en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Décrit les bibliothèques et les outils qui vous permettent de parcourir les vues des arbres des symboles dans l’IDE.

## <a name="related-sections"></a>Sections connexes
- [Extensions de l’éditeur et du service de langage](../../extensibility/editor-and-language-service-extensions.md)

 Donne un aperçu des éditeurs de Visual Studio.

- [Prise en charge du service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md)

 Fournit des informations sur et un lien vers le Visual Studio Debugging SDK, qui contient les informations qui sont nécessaires pour créer et personnaliser les composants de débbugger utilisés pour déboguer les programmes.

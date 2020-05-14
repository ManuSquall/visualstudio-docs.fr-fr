---
title: Mise en œuvre d’un service linguistique hérité1 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707698"
---
# <a name="implementing-a-legacy-language-service"></a>Implémentation d’un service de langage hérité
Vous pouvez utiliser les classes dans le cadre de paquet géré (MPF) pour mettre en œuvre un service linguistique existant qui prend en charge une grande variété de fonctionnalités, telles que la mise en évidence de la syntaxe, l’appariement des accolades et l’achèvement d’IntelliSense.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon de mettre en œuvre un service linguistique, consultez [Editor et Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="in-this-section"></a>Dans cette section
- [Présentation du service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)

 Un aperçu des fonctionnalités du service linguistique qui sont pris en charge dans MPF.

- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Décrit ce qui est nécessaire pour mettre en œuvre un service linguistique en utilisant MPF.

- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Décrit les étapes qui sont nécessaires pour enregistrer un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]service linguistique basé sur le MPF avec .

- [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Décrit les deux analyseurs qui sont nécessaires pour implémenter toutes les fonctionnalités d’un service linguistique en utilisant le MPF.

- [Procédure pas à pas : création d’un service de langage hérité](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Fournit les étapes de base qui sont nécessaires pour mettre en œuvre un service linguistique MPF dans un VSPackage.

- [Procédure pas à pas : obtention d’une liste d’extraits de code installés (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Démontre les techniques de récupération d’une liste de extraits de code installés.

- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)

 Fournit des liens vers des sujets qui détaillent ce qui doit être fait pour mettre en œuvre toutes les fonctionnalités d’un service linguistique en utilisant MPF.

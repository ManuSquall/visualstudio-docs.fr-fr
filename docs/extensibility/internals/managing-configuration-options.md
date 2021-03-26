---
title: Gestion des options de configuration | Microsoft Docs
description: Apprenez à gérer les paramètres de configuration de projet et de solution dans Visual Studio pour contrôler la façon dont votre projet sera généré, empaqueté, déployé et exécuté.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f773148f11a115ee82c8ee84a8d4668001908000
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095197"
---
# <a name="managing-configuration-options"></a>Gestion des options de configuration
Lorsque vous créez un nouveau type de projet, vous devez gérer les paramètres de configuration de projet et de solution qui déterminent la façon dont votre projet sera généré, empaqueté, déployé et exécuté. Les rubriques suivantes traitent de la configuration des projets et des solutions.

## <a name="in-this-section"></a>Dans cette section
- [Vue d’ensemble](../../extensibility/internals/configuration-options-overview.md)

 Décrit comment les projets dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peuvent prendre en charge plusieurs configurations.

- [Pages de propriétés](../../extensibility/internals/property-pages.md)

 Explique que les utilisateurs peuvent afficher et modifier les propriétés dépendantes et les propriétés indépendantes de la configuration de projet à l’aide des pages de propriétés.

- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)

 Fournit des informations sur ce qui est stocké dans les configurations de solution et sur la manière dont les configurations de solution dirigent le comportement des commandes de **démarrage** et de **génération** .

- [Objet de configuration de projet](../../extensibility/internals/project-configuration-object.md)

 Explique comment l’objet de configuration de projet gère l’affichage des informations de configuration dans l’interface utilisateur.

- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)

 Explique comment une liste de configurations de solution pour une solution particulière est gérée par la boîte de dialogue **configurations de solution** .

- [Configuration de projet pour la gestion du déploiement](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Définit l’acte de déploiement et les deux méthodes prennent en charge les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets qui prennent en charge le déploiement.

- [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)

 Explique les processus de génération que chaque configuration peut prendre en charge, ainsi que les interfaces et les méthodes par lesquelles les éléments de sortie peuvent être mis à disposition.

## <a name="related-sections"></a>Sections connexes
- [Types de projets](../../extensibility/internals/project-types.md)

 Fournit une vue d’ensemble des projets en tant que blocs de construction de base de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE). Des liens sont fournis vers des rubriques supplémentaires qui expliquent comment les projets contrôlent la génération et la compilation du code.

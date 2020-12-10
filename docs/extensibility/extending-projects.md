---
title: Extension des projets | Microsoft Docs
description: Découvrez comment créer vos propres types de projets personnalisés dans le kit de développement logiciel (SDK) Visual Studio et comment gérer différents types de solutions Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181acea9a5188ba28a4ef109b5bec0e7c040b5da
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994613"
---
# <a name="extend-projects"></a>Étendre des projets
Les projets et les solutions sont la manière dont Visual Studio organise les fichiers de code et de ressources en unités de compilation et de déploiement. Vous trouverez plus d’informations sur les projets dans les [projets (kit de développement logiciel Visual Studio)](../extensibility/extending-projects.md).

 Vous pouvez créer vos propres types de projets à l’aide du kit de développement logiciel (SDK) Visual Studio et de l’infrastructure de package managée pour les projets, que vous pouvez télécharger au niveau [de l’infrastructure de package managée pour les projets](https://github.com/tunnelvisionlabs/MPFProj10). Pour comprendre comment les projets personnalisés sont implémentés, consultez [nouvelle génération de projet : sous le capot, première partie](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) et [génération de projet : sous le capot, deuxième partie](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Les rubriques de cette section décrivent comment créer des projets personnalisés et comment gérer différents types de solutions Visual Studio.

## <a name="in-this-section"></a>Dans cette section
- [Créer un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md) Décrit comment créer un système de projet personnalisé.

- [Créer un système de projet de base, partie 2](../extensibility/creating-a-basic-project-system-part-2.md) Décrit comment créer un système de projet personnalisé.

- [Enregistrer des données dans les fichiers projet](../extensibility/saving-data-in-project-files.md) Explique comment ajouter au projet (<em>.</em> proj *).

- [Vérifier les sous-types d’un projet au moment de l’exécution](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Explique comment vérifier le sous-type d’un projet au moment de l’exécution.

- [Ajouter et supprimer des pages de propriétés](../extensibility/adding-and-removing-property-pages.md) Explique comment personnaliser les pages de propriétés de votre projet personnalisé.

- [Ajouter un attribut à un élément de projet](../extensibility/adding-an-attribute-to-a-project-item.md) Explique comment ajouter un attribut à un élément de projet personnalisé.

- [Rendre persistante la propriété d’un élément de projet](../extensibility/persisting-the-property-of-a-project-item.md) Explique comment rendre les propriétés d’un élément de projet personnalisé persistantes.

- [Gérer les projets Windows universels](../extensibility/managing-universal-windows-projects.md) Explique comment gérer des projets universels.

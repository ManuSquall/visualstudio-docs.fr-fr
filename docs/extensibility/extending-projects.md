---
title: Extension des projets (fr) Microsoft Docs
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
ms.openlocfilehash: 14108a304cc5f85c9a870bc66804df7daa98f3ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711748"
---
# <a name="extend-projects"></a>Étendre les projets
Les projets et les solutions sont la façon dont Visual Studio organise les fichiers de code et de ressources en unités de compilation et de déploiement. Vous pouvez trouver plus d’informations sur les projets dans [les projets (Visual Studio SDK)](../extensibility/extending-projects.md).

 Vous pouvez créer vos propres types de projets avec le Visual Studio SDK et le cadre de paquet géré pour les projets, que vous pouvez télécharger sur [Le cadre de paquet géré pour les projets](https://github.com/tunnelvisionlabs/MPFProj10). Pour comprendre comment les projets personnalisés sont mis en œuvre, voir [Nouvelle génération de projet: Sous le capot, la première partie](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) et la nouvelle génération de [projet: Sous le capot, la deuxième partie](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Les sujets de cette section décrivent comment créer des projets personnalisés et comment gérer différents types de solution Visual Studio.

## <a name="in-this-section"></a>Contenu de cette section
- [Créer un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md) Décrit comment créer un système de projet personnalisé.

- [Créer un système de projet de base, partie 2](../extensibility/creating-a-basic-project-system-part-2.md) Décrit comment créer un système de projet personnalisé.

- [Enregistrer les données dans les fichiers de projets](../extensibility/saving-data-in-project-files.md) Explique comment ajouter au projet (<em>.</em> fichiers projMD.

- [Vérifier les sous-types d’un projet à l’heure de l’exécution](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Explique comment vérifier le sous-type d’un projet à l’heure de l’exécution.

- [Ajouter et supprimer les pages de propriété](../extensibility/adding-and-removing-property-pages.md) Explique comment personnaliser les pages de propriété pour votre projet personnalisé.

- [Ajouter un attribut à un élément de projet](../extensibility/adding-an-attribute-to-a-project-item.md) Explique comment ajouter un attribut à un élément de projet personnalisé.

- [Persévérer dans la propriété d’un élément de projet](../extensibility/persisting-the-property-of-a-project-item.md) Explique comment persister les propriétés d’un élément de projet personnalisé.

- [Gérer les projets Windows universels](../extensibility/managing-universal-windows-projects.md) Explique comment gérer les projets universels.

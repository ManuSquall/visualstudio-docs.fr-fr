---
title: Extension des projets | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d31da41e3be73f4e2e036841bfc1d96f4476e856
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912803"
---
# <a name="extend-projects"></a>Étendre des projets
Projets et solutions constituent les méthodes que Visual Studio organise les fichiers de code et des ressources en unités de compilation et déploiement. Vous trouverez plus d’informations sur les projets dans [projets (SDK Visual Studio)](../extensibility/extending-projects.md).

 Vous pouvez créer vos propres types de projet avec le SDK Visual Studio et de Managed Package Framework pour les projets, que vous pouvez télécharger sur [Managed Package Framework for Projects](https://github.com/tunnelvisionlabs/MPFProj10). Pour comprendre comment les projets personnalisés sont implémentés, consultez [nouvelle génération de projet : Sous le capot, première partie](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) et [nouvelle génération de projet : Sous le capot, deuxième partie](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Les rubriques de cette section décrivent comment créer des projets personnalisés et comment gérer différents types de solution Visual Studio.

## <a name="in-this-section"></a>Dans cette section
- [Créer un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md) décrit comment créer un système de projet personnalisé.

- [Créer un système de projet de base, partie 2](../extensibility/creating-a-basic-project-system-part-2.md) explique comment créer un système de projet personnalisé.

- [Enregistrer les données dans les fichiers projet](../extensibility/saving-data-in-project-files.md) Explains comment ajouter au projet (<em>.</em> fichiers proj *).

- [Vérifiez les sous-types d’un projet en cours d’exécution](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) explique comment vérifier le sous-type d’un projet au moment de l’exécution.

- [Ajouter et supprimer des pages de propriétés](../extensibility/adding-and-removing-property-pages.md) explique comment personnaliser les pages de propriétés pour votre projet personnalisé.

- [Ajouter un attribut à un élément de projet](../extensibility/adding-an-attribute-to-a-project-item.md) explique comment ajouter un attribut à un élément de projet personnalisé.

- [Rendre persistante la propriété d’un élément de projet](../extensibility/persisting-the-property-of-a-project-item.md) explique comment rendre persistantes les propriétés d’un élément de projet personnalisé.

- [Gérer les projets Windows universels](../extensibility/managing-universal-windows-projects.md) explique comment gérer des projets universelles.
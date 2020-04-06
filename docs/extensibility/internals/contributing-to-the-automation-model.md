---
title: Contribuer au modèle d’automatisation (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d660edc740229c3e91b99e1f59eb37b4e9312098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709268"
---
# <a name="contribute-to-the-automation-model"></a>Contribuer au modèle d’automatisation
Visual Studio fournit un ensemble d’interfaces d’automatisation pour personnaliser l’environnement. Le modèle d’automatisation est le modèle d’objet qui permet aux utilisateurs finaux de créer des add-ins et des extensions Visual Studio.

 En outre, il est approprié pour vous, en tant que développeur VSPackage, de contribuer au modèle d’automatisation; en faisant cela, vous activez les utilisateurs finaux de votre VSPackage pour créer des add-ins et généralement fournir une expérience cohérente modèle utilisateur quand ils utilisent votre VSPackage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Pour rendre l’expérience utilisateur final cohérente, vous pouvez suivre un ensemble de lignes directrices que vous concevez votre VSPackage de sorte que le modèle d’automatisation de votre VSPackage suit les idées en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>Contenu de cette section
- [Aperçu du modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)

 Définit le modèle d’automatisation comme un groupe d’objets apparentés qui contrôlent les principales facettes de l’environnement commun. Cet ensemble d’objets est représenté dans un diagramme du modèle d’automatisation.

- [Fournir l’automatisation pour VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)

 Discute des deux principales façons de fournir l’automatisation de votre VSPackage.

- [Exposer les objets du projet](../../extensibility/internals/exposing-project-objects.md)

 Fournit des instructions étape par étape pour créer des objets spécifiques à VSPackage.

- [Modélisation de projet](../../extensibility/internals/project-modeling.md)

 Explique les objets de projet standard qui sont nécessaires pour créer de l’automatisation pour votre nouveau type de projet et illustre le chemin suivant l’automatisation du projet. Ce sujet fournit également des listes de déclarations et de mise en œuvre pour les classes.

- [Exposer les événements](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Fournit des instructions étape par étape pour créer des événements pour votre modèle d’automatisation.

- [Support d’automatisation pour les pages d’options](../../extensibility/internals/automation-support-for-options-pages.md)

 Décrit comment retourner un objet d’automatisation pour soutenir les propriétés de la boîte de `DTE.Properties` dialogue Options personnalisée **d’un** VSPackage sur le menu De **l’outil** en étendant l’objet.

- [Fournir l’automatisation du code](../../extensibility/internals/providing-automation-for-code.md)

 Explique que la création d’un modèle d’automatisation pour votre code n’est pas nécessaire. Cependant, un lien est fourni dans ce sujet qui fournit des informations perspicaces dans les modèles de code.

- [Comment : Fournir l’automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Explique que fournir l’automatisation est une bonne idée quand vous voulez rendre les objets d’automatisation disponibles sur une fenêtre, et l’environnement ne fournit pas déjà un objet d’automatisation prêt à l’emploi. Discute de l’automatisation des fenêtres d’outils et des fenêtres de documents.

- [Utiliser le modèle d’automatisation](../../extensibility/internals/using-the-automation-model.md)

 Fournit deux exemples de code qui montrent comment un consommateur d’automatisation obtient les objets d’automatisation de projet initial.

- [Automatisation pour les objets Configuration et SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Fournit des informations sur l’automatisation des objets Configuration et SelectedItems.

## <a name="reference"></a>Informations de référence
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>Fournit un échantillon de code qui montre comment un VSPackage participe au modèle d’objet d’automatisation DTE. Listes des paramètres, des valeurs de retour et des remarques sélectionnées.

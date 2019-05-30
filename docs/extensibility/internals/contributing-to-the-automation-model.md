---
title: Contribution au modèle Automation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47e6686c82dcb0272fa9b3b3c4d3b7c73afe4475
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335444"
---
# <a name="contribute-to-the-automation-model"></a>Contribuer au modèle automation
Visual Studio fournit un ensemble d’interfaces d’automatisation pour la personnalisation de l’environnement. Le modèle automation est le modèle objet qui permet aux utilisateurs finaux de créer des compléments Visual Studio et des extensions.

 En outre, il est approprié pour vous, en tant que VSPackage développeur, de contribuer au modèle automation ; Ce faisant, vous permettez aux utilisateurs de votre package Visual Studio pour créer des compléments et offrira une expérience de modèle utilisateur cohérente lorsqu’ils utilisent votre VSPackage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Pour que l’utilisateur final expérience soit cohérente, vous pouvez suivre un ensemble d’instructions lorsque vous concevez votre VSPackage afin que le modèle automation pour votre VSPackage suit les idées dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>Dans cette section
- [Vue d’ensemble du modèle Automation](../../extensibility/internals/automation-model-overview.md)

 Définit le modèle automation comme un groupe connexe d’objets qui contrôlent les aspects de l’environnement du common. Cet ensemble d’objets est représenté dans un diagramme du modèle automation.

- [Fournir l’automatisation pour VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)

 Décrit les deux méthodes principales pour fournir l’automatisation pour votre VSPackage.

- [Exposer des objets du projet](../../extensibility/internals/exposing-project-objects.md)

 Fournit des instructions détaillées pour la création d’objets VSPackage spécifiques.

- [Modélisation de projet](../../extensibility/internals/project-modeling.md)

 Explique les objets de projet standard qui sont nécessaires pour créer l’automation pour votre nouveau type de projet et illustre le chemin d’accès qui suit d’automation de projet. Cette rubrique fournit également des annonces de déclarations et d’implémentation pour les classes.

- [Exposer des événements](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Fournit des instructions détaillées pour la création d’événements pour votre modèle automation.

- [Automation prend en charge pour les pages options](../../extensibility/internals/automation-support-for-options-pages.md)

 Décrit comment retourner un objet automation pour prendre en charge les propriétés d’un VSPackage personnalisée du **Options** boîte de dialogue sur le **outil** menu en étendant la `DTE.Properties` objet.

- [Fournir l’automatisation pour le code](../../extensibility/internals/providing-automation-for-code.md)

 Explique que la création d’un modèle automation pour votre code n’est pas requise. Toutefois, un lien est fourni dans cette rubrique qui fournit des informations pertinentes dans les modèles de code.

- [Guide pratique pour Fournir l’automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Explique que grâce à l’automatisation est une bonne idée chaque fois que vous souhaitez rendre disponibles les objets automation sur une fenêtre et l’environnement ne fournit pas déjà un objet automation prêtes à l’emploi. Décrit l’automation pour les fenêtres Outil et fenêtres de document.

- [Utiliser le modèle automation](../../extensibility/internals/using-the-automation-model.md)

 Fournit deux exemples de code qui montrent la façon dont un utilisateur d’automation Obtient le projet initial objets automation.

- [Automation pour les objets de Configuration et SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Fournit des informations sur l’automatisation pour les objets de Configuration et SelectedItems.

## <a name="reference"></a>Référence
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Fournit un exemple de code qui montre comment un VSPackage participe le modèle d’objet automation DTE. Répertorie les paramètres, les valeurs de retour et les remarques sélectionnés.

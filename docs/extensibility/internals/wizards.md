---
title: Les sorciers Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d65cf2dcc10380b0ac750c8e1b0e7fd56eab95b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703207"
---
# <a name="wizards"></a>Assistants
Après avoir créé un assistant, vous voulez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] généralement l’ajouter à l’environnement de développement intégré (IDE) afin que d’autres puissent l’utiliser. L’assistant ajouté apparaît alors dans les boîtes de dialogue **Add New Project** ou Ajouter de nouveaux **éléments.** Pour voir le **nouveau projet Ou** ajouter de nouvelles boîtes de dialogue **d’élément,** cliquez à droite sur une solution ouverte dans **Solution Explorer**, pointez **ajouter,** puis cliquez sur **nouveau projet** ou **nouvel article**.

 Les assistants peuvent [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] être implémenté pour permettre aux utilisateurs de choisir à partir d’une vue d’arbre des valeurs disponibles lorsqu’ils ouvrent la boîte de dialogue **Add New Project** ou la boîte de dialogue Add New **Item,** ou lorsqu’ils cliquez à droite sur un élément dans **Solution Explorer**.

 Dans votre assistant, vous pouvez fournir la possibilité de localisation du nom d’un nouveau projet ou ites, et vous pouvez déterminer l’icône que les utilisateurs verront quand ils choisissent l’assistant. Vous pouvez également contrôler l’ordre dans lequel de nouveaux éléments apparaissent par rapport à d’autres articles disponibles; articles n’ont pas besoin d’être organisés par ordre alphabétique.

 Vous pouvez également fournir un sorcier qui commence différemment, basé sur des paramètres personnalisés qui sont transmis à l’assistant quand il est ouvert.

 Les sujets de cette section discutent des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fichiers que vous implémentez pour provoquer le **nouveau projet Et** ajouter de nouvelles boîtes de dialogue **d’élément** pour inscrire votre assistant parmi les assistants et les modèles disponibles, et les exigences que votre assistant doit satisfaire pour fonctionner correctement dans l’IDE.

## <a name="in-this-section"></a>Dans cette section
- [Fichiers de description de répertoire de modèles (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Fournit un aperçu des fichiers de description d’annuaire de modèle et explique comment ils fonctionnent dans les dossiers d’affichage, les fichiers de .vsz de magicien, et les fichiers de modèle qui sont associés à un projet dans les boîtes de dialogue.

- [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

 Explique comment l’IDE démarre les assistants et répertorie les trois parties du fichier .vsz.

- [Interface de l’Assistant (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Décrit l’interface que les `IDTWizard` sorciers doivent mettre en œuvre pour travailler dans l’IDE.

- [Paramètres contextuelles](../../extensibility/internals/context-parameters.md)

 Explique comment les assistants sont mis en œuvre et ce qui se produit lorsque l’IDE passe Paramètres contexte à la mise en œuvre.

- [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)

 Explique comment utiliser des paramètres personnalisés pour contrôler le fonctionnement de l’assistant après le début de l’assistant.

## <a name="related-sections"></a>Sections connexes
- [Types de projets](../../extensibility/internals/project-types.md)

 Fournit des liens vers d’autres sujets qui offrent des informations sur la façon de concevoir de nouveaux types de projets.

- [Extension des projets](../../extensibility/extending-projects.md)

 Décrit comment utiliser des projets et des solutions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour organiser des fichiers de code et de ressources, et comment implémenter le contrôle de code source.

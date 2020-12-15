---
title: Assistants | Microsoft Docs
description: Découvrez comment répertorier votre Assistant parmi les assistants et les modèles disponibles dans Visual Studio et à propos des spécifications que votre assistant doit remplir dans l’IDE.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f367723a3c819635f2d7cf20ed812a36cda12830
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487749"
---
# <a name="wizards"></a>Assistants
Une fois que vous avez créé un Assistant, vous souhaitez généralement l’ajouter à l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE) afin que d’autres utilisateurs puissent l’utiliser. L’Assistant ajouté apparaît alors dans les boîtes de dialogue **Ajouter un nouveau projet** ou **Ajouter un nouvel élément** . Pour afficher les boîtes de dialogue **Ajouter un nouveau projet** ou **Ajouter un nouvel élément** , cliquez avec le bouton droit sur une solution ouverte dans **Explorateur de solutions**, pointez sur **Ajouter**, puis cliquez sur **nouveau projet** ou **nouvel élément**.

 Les assistants peuvent être implémentés dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour permettre aux utilisateurs de sélectionner des valeurs disponibles dans une arborescence lorsqu’ils ouvrent la boîte de dialogue **Ajouter un nouveau projet** ou **Ajouter un nouvel élément** , ou lorsqu’ils cliquent avec le bouton droit sur un élément dans **Explorateur de solutions**.

 Dans votre Assistant, vous pouvez fournir la possibilité de localiser le nom d’un nouveau projet ou ITES, et vous pouvez déterminer l’icône que les utilisateurs verront lorsqu’ils sélectionneront l’Assistant. Vous pouvez également contrôler l’ordre dans lequel les nouveaux éléments s’affichent par rapport aux autres éléments disponibles. Il n’est pas nécessaire d’organiser les éléments par ordre alphabétique.

 Vous pouvez également fournir un assistant qui démarre différemment, en fonction des paramètres personnalisés qui sont passés à l’Assistant lorsqu’il est ouvert.

 Les rubriques de cette section décrivent les fichiers que vous implémentez pour que les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] boîtes de dialogue **Ajouter un nouveau projet** et **Ajouter un nouvel élément** permettent de répertorier votre Assistant parmi les assistants et les modèles disponibles, ainsi que les spécifications que votre assistant doit respecter pour fonctionner correctement dans l’IDE.

## <a name="in-this-section"></a>Dans cette section
- [Fichiers de description de répertoire de modèles (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Fournit une vue d’ensemble des fichiers de description de répertoire de modèle et explique comment ils fonctionnent dans l’IDE pour afficher des dossiers, des fichiers Assistant. vsz et des fichiers modèles associés à un projet dans les boîtes de dialogue.

- [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

 Explique comment l’IDE démarre les assistants et répertorie les trois parties du fichier. vsz.

- [Interface de l’Assistant (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Décrit l' `IDTWizard` interface que les assistants doivent implémenter pour fonctionner dans l’IDE.

- [Paramètres de contexte](../../extensibility/internals/context-parameters.md)

 Explique comment les assistants sont implémentés et ce qui se produit lorsque l’IDE transmet les paramètres de contexte à l’implémentation.

- [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)

 Explique comment utiliser des paramètres personnalisés pour contrôler le fonctionnement de l’Assistant après le démarrage de l’Assistant.

## <a name="related-sections"></a>Sections connexes
- [Types de projets](../../extensibility/internals/project-types.md)

 Fournit des liens vers des rubriques supplémentaires qui fournissent des informations sur la façon de concevoir de nouveaux types de projets.

- [Extension des projets](../../extensibility/extending-projects.md)

 Décrit comment utiliser des projets et des solutions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour organiser des fichiers de code et de ressources, et comment implémenter le contrôle de code source.

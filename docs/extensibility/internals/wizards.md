---
title: Assistants | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 838b7cac850b8e7eb3401065cf13202d3a3a40ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="wizards"></a>Assistants
Après avoir créé un Assistant, vous souhaiterez généralement ajouter à la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] développement environnement intégré (IDE) afin que d’autres peuvent l’utiliser. L’Assistant Ajout apparaît alors dans le **ajouter un nouveau projet** ou **ajouter un nouvel élément** boîtes de dialogue. Pour voir les **ajouter un nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue zones, cliquez sur une solution ouverte dans **l’Explorateur de solutions**, pointez sur **ajouter**, et puis cliquez sur **nouveau projet** ou **un nouvel élément**.  
  
 Assistants peuvent être implémentées dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour permettre aux utilisateurs sélectionnez dans l’arborescence de valeurs disponibles lorsqu’ils ouvrent le **ajouter un nouveau projet** boîte de dialogue ou le **ajouter un nouvel élément** boîte de dialogue, ou quand ils sur un élément de **l’Explorateur de solutions**.  
  
 Dans l’Assistant, vous pouvez fournir l’option de localisation du nom d’un nouveau projet ou les deux, et vous pouvez déterminer l’icône que les utilisateurs verront lorsqu’ils sélectionnent l’Assistant. Vous pouvez également contrôler l’ordre dans lequel les nouveaux éléments apparaissent par rapport aux autres éléments disponibles ; éléments n’ont pas à être organisées par ordre alphabétique.  
  
 Vous pouvez également fournir un Assistant démarre différemment, en fonction des paramètres personnalisés qui sont passés à l’Assistant lorsqu’il est ouvert.  
  
 Les rubriques de cette section décrivent les fichiers que vous implémentez pour provoquer le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **ajouter un nouveau projet** et **ajouter un nouvel élément** boîtes de dialogue pour votre Assistant parmi les Assistants disponibles et les modèles de liste et les exigences que votre Assistant doit satisfaire pour fonctionner correctement dans l’IDE.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Fichiers de description de répertoire de modèles (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Fournit une vue d’ensemble de quel modèle Active les fichiers de description et explique comment ils fonctionnent dans l’IDE pour afficher les dossiers, les fichiers .vsz de l’Assistant et les fichiers de modèle qui sont associés à un projet dans les boîtes de dialogue.  
  
 [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Explique comment l’IDE démarre les Assistants et répertorie les trois parties du fichier .vsz.  
  
 [Interface de l’Assistant (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Décrit le `IDTWizard` interface Assistants doivent implémenter pour travailler dans l’IDE.  
  
 [Paramètres de contexte](../../extensibility/internals/context-parameters.md)  
 Explique comment les Assistants sont implémentées et que se passe-t-il lorsque l’IDE passe des paramètres de contexte à l’implémentation.  
  
 [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)  
 Explique comment utiliser les paramètres personnalisés pour contrôler le fonctionnement de l’Assistant une fois que l’Assistant est démarré.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit des liens vers des rubriques supplémentaires qui fournissent des informations sur la façon de concevoir de nouveaux types de projet.  
  
 [Procédure pas à pas : Création d’un Assistant](http://msdn.microsoft.com/Library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Montre comment créer un Assistant.  
  
 [Extension des projets](../../extensibility/extending-projects.md)  
 Décrit comment utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets et solutions possibles pour organiser les fichiers de code et les fichiers de ressources et comment implémenter le contrôle de code source.
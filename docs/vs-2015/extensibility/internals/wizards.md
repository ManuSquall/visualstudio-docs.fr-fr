---
title: Assistants | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbf2eceeb3ae8a3870954d53f8d85c46f3322d24
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747606"
---
# <a name="wizards"></a>Assistants
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Après avoir créé un Assistant, vous souhaiterez généralement ajouter à la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] développement environnement intégré (IDE) afin que d’autres peuvent l’utiliser. L’Assistant Ajout apparaît alors dans le **ajouter un nouveau projet** ou **ajouter un nouvel élément** boîtes de dialogue. Pour voir les **ajouter un nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue zones, cliquez sur une solution ouverte dans **l’Explorateur de solutions**, pointez sur **ajouter**, et puis cliquez sur **nouveau projet** ou **un nouvel élément**.  
  
 Assistants peuvent être implémentées dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour permettre aux utilisateurs sélectionnez à partir d’une arborescence de valeurs disponibles lorsqu’ils ouvrent le **ajouter un nouveau projet** boîte de dialogue ou la **ajouter un nouvel élément** boîte de dialogue, ou quand ils droit un élément dans **l’Explorateur de solutions**.  
  
 Dans l’Assistant, vous pouvez fournir la possibilité de localisation du nom d’un nouveau projet ou les ite, et vous pouvez déterminer l’icône que les utilisateurs verront lorsqu’ils sélectionnent l’Assistant. Vous pouvez également contrôler l’ordre dans lequel les nouveaux éléments apparaissent par rapport à d’autres éléments disponibles ; éléments n’ont pas d’être organisées par ordre alphabétique.  
  
 Vous pouvez également fournir un Assistant démarre différemment, selon les paramètres personnalisés qui sont passés à l’Assistant lorsqu’il est ouvert.  
  
 Les rubriques de cette section traitent les fichiers que vous implémentez pour provoquer la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **ajouter un nouveau projet** et **ajouter un nouvel élément** boîtes de dialogue pour votre Assistant parmi les Assistants disponibles et les modèles, liste et les exigences de votre Assistant doit respecter pour fonctionner correctement dans l’IDE.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Fichiers de description de répertoire de modèles (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Fournit une vue d’ensemble de quel modèle les fichiers de description de répertoire et explique leur fonctionnement dans l’IDE pour afficher les dossiers, les fichiers .vsz de l’Assistant et les fichiers de modèle qui sont associés à un projet dans les boîtes de dialogue.  
  
 [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Explique comment l’IDE démarre les Assistants et répertorie les trois parties du fichier .vsz.  
  
 [Interface de l’Assistant (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Décrit le `IDTWizard` interface Assistants doivent implémenter pour travailler dans l’IDE.  
  
 [Paramètres de contexte](../../extensibility/internals/context-parameters.md)  
 Explique comment les Assistants sont implémentés et ce qui se produit lorsque l’IDE transmet les paramètres de contexte à l’implémentation.  
  
 [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)  
 Explique comment utiliser les paramètres personnalisés pour contrôler le fonctionnement de l’Assistant une fois que l’Assistant est démarré.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit des liens vers des rubriques supplémentaires qui offrent des informations sur la façon de concevoir de nouveaux types de projet.  
  
 [Procédure pas à pas : Création d’un Assistant](http://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Illustre comment créer un Assistant.  
  
 [Extension des projets](../../extensibility/extending-projects.md)  
 Décrit comment utiliser des projets et des solutions [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour organiser des fichiers de code et de ressources, et comment implémenter le contrôle de code source.


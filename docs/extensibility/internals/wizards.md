---
title: Assistants | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: af0466ea3c11b75090e45cb9b408ed0723cd8a6f
ms.lasthandoff: 02/22/2017

---
# <a name="wizards"></a>Assistants
Après avoir créé un Assistant, vous souhaiterez généralement ajouter à le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] intégré l’environnement de développement (IDE) afin que d’autres puissent l’utiliser. L’Assistant Ajout apparaît alors dans la **ajouter un nouveau projet** ou **ajouter un nouvel élément** boîtes de dialogue. Pour voir les **ajouter un nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue zones, cliquez sur une solution ouverte dans **l’Explorateur de solutions**, pointez sur **ajouter**, puis cliquez sur **nouveau projet** ou **un nouvel élément**.  
  
 Assistants peuvent être implémentées dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour permettre aux utilisateurs sélectionnez dans l’arborescence de valeurs disponibles lorsqu’ils ouvrent le **ajouter un nouveau projet** boîte de dialogue ou la **ajouter un nouvel élément** boîte de dialogue, ou lorsqu’ils sur un élément de **l’Explorateur de solutions**.  
  
 Dans l’Assistant, vous pouvez fournir la possibilité de localiser le nom d’un nouveau projet ou les deux, et vous pouvez déterminer l’icône que voient les utilisateurs lorsqu’ils sélectionnent l’Assistant. Vous pouvez également contrôler l’ordre dans lequel les nouveaux éléments apparaissent par rapport aux autres éléments disponibles ; éléments n’ont pas à être organisées par ordre alphabétique.  
  
 Vous pouvez également fournir un Assistant démarre différemment, en fonction des paramètres personnalisés qui sont passés à l’Assistant lorsqu’il est ouvert.  
  
 Les rubriques de cette section traitent les fichiers que vous implémentez pour provoquer la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **ajouter un nouveau projet** et **ajouter un nouvel élément** votre Assistant entre les modèles et les Assistants disponibles et la configuration requise pour fonctionner correctement dans l’IDE que votre Assistant liste des boîtes de dialogue.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Description du modèle active (. Fichiers VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Présente le modèle les fichiers de description active et explique comment ils fonctionnent dans l’IDE pour afficher les dossiers et fichiers de modèle qui sont associés à un projet dans les boîtes de dialogue fichiers .vsz de l’Assistant.  
  
 [Assistant (. Fichier vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Explique comment l’IDE démarre les Assistants et répertorie les trois parties du fichier .vsz.  
  
 [Interface de l’Assistant (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Décrit le `IDTWizard` interface Assistants doivent implémenter pour travailler dans l’IDE.  
  
 [Paramètres de contexte](../../extensibility/internals/context-parameters.md)  
 Explique comment les Assistants sont implémentées et que se passe-t-il lorsque l’IDE passe les paramètres de contexte à l’implémentation.  
  
 [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)  
 Explique comment utiliser les paramètres personnalisés pour contrôler le fonctionnement de l’Assistant une fois que l’Assistant est démarré.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit des liens vers des rubriques supplémentaires qui offrent des informations sur la conception de nouveaux types de projet.  
  
 [Procédure pas à pas : Création d’un Assistant](http://msdn.microsoft.com/Library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Montre comment créer un Assistant.  
  
 [Étendre des projets](../../extensibility/extending-projects.md)  
 Décrit comment utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets et solutions pour organiser les fichiers de code et les fichiers de ressources, l’implémentation de contrôle de code source.

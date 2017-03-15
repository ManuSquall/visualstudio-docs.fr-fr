---
title: "Qui contribuent au mod&#232;le Automation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Automation (Visual Studio SDK)"
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Qui contribuent au mod&#232;le Automation
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio fournit un ensemble d'interfaces d'automatisation pour la personnalisation de l'environnement. Le modèle d'automatisation est le modèle objet qui permet aux utilisateurs finaux de créer des compléments Visual Studio et des extensions.  
  
 En outre, il est approprié pour vous, en tant que développeur VSPackage, contribuer au modèle automation ; Ce faisant, vous permettez aux utilisateurs de votre package VS pour créer des compléments et offrira une expérience cohérente modèle lorsqu'ils utilisent votre package VS dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Pour rendre l'utilisateur final expérience cohérente, vous pouvez suivre un ensemble d'instructions lorsque vous concevez votre VSPackage afin que le modèle automation pour votre VSPackage suit les idées dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Dans cette section  
 [Vue d’ensemble du modèle Automation](../../extensibility/internals/automation-model-overview.md)  
 Définit le modèle automation comme un associés des groupes d'objets qui contrôlent les aspects de l'environnement du common. Cet ensemble d'objets est représenté dans un diagramme du modèle automation.  
  
 [Grâce à l’automatisation pour les packages VS](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Décrit les deux principaux moyens de fournir l'automatisation pour votre VSPackage.  
  
 [Exposer des objets de projet](../../extensibility/internals/exposing-project-objects.md)  
 Fournit des instructions détaillées pour la création d'objets spécifiques VSPackage.  
  
 [Modélisation de projet](../../extensibility/internals/project-modeling.md)  
 Décrit les objets de projet standard qui sont nécessaires pour créer une automatisation pour votre nouveau type de projet et illustre le chemin d'accès qui le suit d'automation de projet. Cette rubrique fournit également des listes de déclaration et l'implémentation de classes.  
  
 [Exposition d'événements](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Fournit des instructions détaillées pour la création d'événements pour votre modèle automation.  
  
 [Prise en charge d'Automation pour les Pages d'Options](../../extensibility/internals/automation-support-for-options-pages.md)  
 Décrit comment retourner un objet automation pour prendre en charge les propriétés d'un VSPackage personnalisée du **Options** boîte de dialogue sur le **outil** menu en étendant le `DTE.Properties` objet.  
  
 [Grâce à l'automatisation pour le Code](../../extensibility/internals/providing-automation-for-code.md)  
 Explique que la création d'un modèle automation de votre code n'est pas nécessaire. Toutefois, un lien est fourni dans cette rubrique qui fournit des informations pertinentes dans les modèles de code.  
  
 [Comment : fournir l'automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Explique que grâce à l'automatisation est une bonne idée, chaque fois que vous souhaitez rendre disponibles les objets automation dans une fenêtre et l'environnement ne fournit pas déjà un objet automation prêts à l'emploi. Décrit l'automation pour les fenêtres Outil et les fenêtres de document.  
  
 [À l'aide de le modèle Automation](../../extensibility/internals/using-the-automation-model.md)  
 Fournit deux exemples de code qui montrent comment un client automation Obtient le projet initial objets automation.  
  
 [Automatisation de la Configuration et les objets SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Fournit des informations sur les Options de Configuration de l'automatisation et l'automatisation pour les éléments sélectionnés.  
  
## Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fournit un exemple de code qui montre comment un VSPackage est inclus dans le modèle d'objet automation DTE. Répertorie les paramètres et valeurs de retour Notes sélectionnée.  
  
## Rubriques connexes
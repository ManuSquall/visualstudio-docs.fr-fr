---
title: "Qui contribuent au modèle Automation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5907f540e5f81e26b7d184352e3c38531ec5da66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="contributing-to-the-automation-model"></a>Qui contribuent au modèle Automation
Visual Studio fournit un ensemble d’interfaces d’automation pour la personnalisation de l’environnement. Le modèle automation est le modèle objet qui permet aux utilisateurs finaux de créer des extensions et les compléments Visual Studio.  
  
 En outre, elle vous convient, un développeur de VSPackage, qui contribuent au modèle automation ; Ce faisant, vous activez les utilisateurs finaux de votre VSPackage pour créer des compléments et généralement l’expérience utilisateur cohérente modèle lorsqu’ils utilisent votre VSPackage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Pour que l’utilisateur final expérience soit cohérente, vous pouvez suivre un ensemble d’instructions lorsque vous concevez votre VSPackage afin que le modèle automation pour votre VSPackage suit les idées dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)  
 Définit le modèle automation comme des groupes d’objets qui contrôlent les aspects de l’environnement du common connexes. Cet ensemble d’objets est représenté dans un diagramme du modèle automation.  
  
 [Fourniture de l’automatisation pour VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Décrit les deux façons pour fournir l’automatisation pour votre VSPackage.  
  
 [Exposition des objets de projet](../../extensibility/internals/exposing-project-objects.md)  
 Fournit des instructions détaillées pour la création d’objets VSPackage spécifiques.  
  
 [Modélisation de projet](../../extensibility/internals/project-modeling.md)  
 Explique les objets du projet standard qui sont requises pour créer l’automation pour votre nouveau type de projet et illustre le chemin d’accès qui suit d’automation de projet. Cette rubrique fournit également des annonces de déclarations et d’implémentation pour les classes.  
  
 [Exposant les événements](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Fournit des instructions détaillées pour la création d’événements pour votre modèle automation.  
  
 [Prise en charge de l’automatisation pour les pages Options](../../extensibility/internals/automation-support-for-options-pages.md)  
 Décrit comment retourner un objet automation pour prendre en charge les propriétés d’un VSPackage personnalisée du **Options** boîte de dialogue sur le **outil** menu en étendant le `DTE.Properties` objet.  
  
 [Fourniture de l’automatisation pour le code](../../extensibility/internals/providing-automation-for-code.md)  
 Explique que la création d’un modèle automation pour votre code n’est pas requise. Toutefois, un lien est fourni dans cette rubrique qui fournit des informations pertinentes dans les modèles de code.  
  
 [Guide pratique pour fournir l’automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Explique que grâce à l’automatisation est une bonne idée, chaque fois que vous souhaitez rendre disponibles les objets automation dans une fenêtre et l’environnement ne fournit pas déjà un objet automation prêts à l’emploi. Décrit l’automation pour les fenêtres Outil et fenêtres de document.  
  
 [Utilisation du modèle d’automatisation](../../extensibility/internals/using-the-automation-model.md)  
 Fournit deux exemples de code qui montrent comment un client automation Obtient le projet initial objets automation.  
  
 [Automatisation de la configuration et des objets SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Fournit des informations sur l’automation pour les Options de Configuration et d’automation pour les éléments sélectionnés.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fournit un exemple de code qui montre comment un VSPackage est inclus dans le modèle d’objet automation DTE. Répertorie les paramètres et valeurs de retour sélectionné de la section Notes.  
  
## <a name="related-sections"></a>Rubriques connexes
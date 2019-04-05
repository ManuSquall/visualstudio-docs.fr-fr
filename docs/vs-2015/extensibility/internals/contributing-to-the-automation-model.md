---
title: Contribution au modèle Automation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c84ea078f9b7c1268b765111cc400f6e51b783f1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952553"
---
# <a name="contributing-to-the-automation-model"></a>Contribution au modèle d’automatisation
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio fournit un ensemble d’interfaces d’automatisation pour la personnalisation de l’environnement. Le modèle automation est le modèle objet qui permet aux utilisateurs finaux de créer des compléments Visual Studio et des extensions.  
  
 En outre, il est approprié pour vous, en tant que VSPackage développeur, de contribuer au modèle automation ; Ce faisant, vous permettez aux utilisateurs de votre package Visual Studio pour créer des compléments et offrira une expérience de modèle utilisateur cohérente lorsqu’ils utilisent votre VSPackage dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Pour que l’utilisateur final expérience soit cohérente, vous pouvez suivre un ensemble d’instructions lorsque vous concevez votre VSPackage afin que le modèle automation pour votre VSPackage suit les idées dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)  
 Définit le modèle automation comme un groupe connexe d’objets qui contrôlent les aspects de l’environnement du common. Cet ensemble d’objets est représenté dans un diagramme du modèle automation.  
  
 [Fourniture de l’automatisation pour VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Décrit les deux méthodes principales pour fournir l’automatisation pour votre VSPackage.  
  
 [Exposition des objets de projet](../../extensibility/internals/exposing-project-objects.md)  
 Fournit des instructions détaillées pour la création d’objets VSPackage spécifiques.  
  
 [Modélisation de projet](../../extensibility/internals/project-modeling.md)  
 Explique les objets de projet standard qui sont nécessaires pour créer l’automation pour votre nouveau type de projet et illustre le chemin d’accès qui suit d’automation de projet. Cette rubrique fournit également des annonces de déclarations et d’implémentation pour les classes.  
  
 [Exposition d’événements](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Fournit des instructions détaillées pour la création d’événements pour votre modèle automation.  
  
 [Prise en charge de l’automatisation pour les pages Options](../../extensibility/internals/automation-support-for-options-pages.md)  
 Décrit comment retourner un objet automation pour prendre en charge les propriétés d’un VSPackage personnalisée du **Options** boîte de dialogue sur le **outil** menu en étendant la `DTE.Properties` objet.  
  
 [Fourniture de l’automatisation pour le code](../../extensibility/internals/providing-automation-for-code.md)  
 Explique que la création d’un modèle automation pour votre code n’est pas requise. Toutefois, un lien est fourni dans cette rubrique qui fournit des informations pertinentes dans les modèles de code.  
  
 [Guide pratique pour Fournir l’automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Explique que grâce à l’automatisation est une bonne idée chaque fois que vous souhaitez rendre disponibles les objets automation sur une fenêtre et l’environnement ne fournit pas déjà un objet automation prêtes à l’emploi. Décrit l’automation pour les fenêtres Outil et fenêtres de document.  
  
 [Utilisation du modèle d’automatisation](../../extensibility/internals/using-the-automation-model.md)  
 Fournit deux exemples de code qui montrent la façon dont un utilisateur d’automation Obtient le projet initial objets automation.  
  
 [Automatisation de la configuration et des objets SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Fournit des informations sur l’automatisation des Options de Configuration et l’automatisation des éléments sélectionnés.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fournit un exemple de code qui montre comment un VSPackage participe le modèle d’objet automation DTE. Répertorie les paramètres, les valeurs de retour et les remarques sélectionnés.  
  
## <a name="related-sections"></a>Rubriques connexes

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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196999"
---
# <a name="contributing-to-the-automation-model"></a>Contribution au modèle d’automatisation
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio fournit un ensemble d’interfaces d’automatisation pour la personnalisation de l’environnement. Le modèle Automation est le modèle objet qui permet aux utilisateurs finaux de créer des compléments et des extensions Visual Studio.  
  
 En outre, il convient, en tant que développeur VSPackage, de contribuer au modèle Automation. en procédant ainsi, vous permettez aux utilisateurs finaux de votre VSPackage de créer des compléments et de fournir en général une expérience de modèle utilisateur cohérente lorsqu’ils utilisent votre VSPackage dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Pour rendre l’expérience de l’utilisateur final cohérente, vous pouvez suivre un ensemble d’instructions lors de la conception de votre VSPackage afin que le modèle Automation pour votre VSPackage suive les idées dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)  
 Définit le modèle Automation en tant que groupes d’objets connexes qui contrôlent les facettes principales de l’environnement commun. Cet ensemble d’objets est représenté dans un diagramme du modèle Automation.  
  
 [Fourniture de l’automatisation pour VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Décrit les deux principales façons de fournir une automatisation pour votre VSPackage.  
  
 [Exposition des objets de projet](../../extensibility/internals/exposing-project-objects.md)  
 Fournit des instructions pas à pas pour la création d’objets spécifiques au VSPackage.  
  
 [Modélisation de projet](../../extensibility/internals/project-modeling.md)  
 Explique les objets de projet standard qui sont requis pour créer l’automatisation pour votre nouveau type de projet et illustre le chemin d’accès de l’Automation de projet. Cette rubrique fournit également des listes de déclarations et d’implémentation pour les classes.  
  
 [Exposition d’événements](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Fournit des instructions pas à pas pour la création d’événements pour votre modèle Automation.  
  
 [Prise en charge de l’automatisation pour les pages Options](../../extensibility/internals/automation-support-for-options-pages.md)  
 Décrit comment retourner un objet Automation pour les propriétés de prise en charge de la boîte de dialogue **options** personnalisées d’un VSPackage dans le menu **outil** en étendant l' `DTE.Properties` objet.  
  
 [Fourniture de l’automatisation pour le code](../../extensibility/internals/providing-automation-for-code.md)  
 Explique que la création d’un modèle Automation pour votre code n’est pas obligatoire. Toutefois, un lien est fourni dans cette rubrique qui fournit des informations pertinentes dans les modèles de code.  
  
 [Guide pratique pour fournir l’automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Explique que l’automatisation est une bonne idée quand vous souhaitez rendre des objets Automation disponibles dans une fenêtre, et que l’environnement ne fournit pas déjà un objet Automation prêt à l’emploi. Traite de l’automatisation pour les fenêtres outil et les fenêtres de document.  
  
 [Utilisation du modèle d’automatisation](../../extensibility/internals/using-the-automation-model.md)  
 Fournit deux exemples de code qui montrent comment un consommateur Automation obtient les objets Automation de projet initiaux.  
  
 [Automatisation de la configuration et des objets SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Fournit des informations sur l’automatisation pour les options de configuration et l’automatisation pour les éléments sélectionnés.  
  
## <a name="reference"></a>Informations de référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fournit un exemple de code qui montre comment un VSPackage participe au modèle objet d’automatisation DTE. Répertorie les paramètres, les valeurs de retour et les notes sélectionnées.  
  
## <a name="related-sections"></a>Sections connexes

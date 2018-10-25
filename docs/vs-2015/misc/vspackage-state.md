---
title: État du VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: douge
ms.openlocfilehash: 0364d7190244217bef50b50b60462d69e1fc145c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895208"
---
# <a name="vspackage-state"></a>État du VSPackage
De nombreux facteurs déterminent le jeu de valeurs persistantes ou l’état d’un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] application.  
  
- Les projets ont des propriétés de configuration et de projet.  
  
- Solutions ont des propriétés.  
  
- Paramètres utilisateur déterminent la taille et la position des fenêtres de document, les fenêtres Outil, état d’ancrage et raccourcis clavier.  
  
- Applications peuvent avoir des options qui définit un utilisateur.  
  
- Les objets créés par une application peuvent avoir leurs propres propriétés.  
  
  Voici quelques-unes des méthodes qui un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] état de l’application peut être géré :  
  
- Via les pages de propriétés de projet et solution.  
  
- Via le **Assistant Importation et exportation paramètres**, ce qui permet à un utilisateur déplacer les paramètres d’un ordinateur à un autre.  
  
- Via le **Options** boîte de dialogue qui inclut des options relatives aux applications.  
  
- Via le **propriétés** fenêtre, qui expose les propriétés d’objets.  
  
- Grâce à l’automatisation. Une application peut accéder à des propriétés VSPackage et les objets qui ont été exposées à Automation.  
  
  Sous-jacent de l’état de l’application est différents mécanismes de persistance qui permettent l’état de l’application à être enregistré et restauré.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge de la persistance de l’état](../misc/support-for-state-persistence.md)  
 Répertorie les stratégies couramment utilisées pour enregistrer, restaurer et réinitialiser l’état d’un VSPackage.  
  
 [Options et pages Options](../extensibility/internals/options-and-options-pages.md)  
 Présente des pages d’Options générales et personnalisées et explique comment les implémenter.  
  
 [Création d’une page d’options](../extensibility/creating-an-options-page.md)  
 Explique comment créer deux pages d’Options, une page simple et une page personnalisée.  
  
 [Prise en charge des catégories de paramètres](../misc/support-for-settings-categories.md)  
 Décrit les paramètres utilisateur et comment elles sont créées et conservées.  
  
 [Création d’une catégorie de paramètres](../extensibility/creating-a-settings-category.md)  
 Explique comment créer un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] catégorie de paramètres et l’utiliser pour enregistrer les valeurs et de restaurer les valeurs à partir d’un fichier de paramètres.  
  
 [Extension des propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)  
 Explique comment afficher et modifier la valeur d’un objet dans le **propriétés** fenêtre.  
  
 [Exposition des propriétés dans la fenêtre Propriétés](../extensibility/exposing-properties-to-the-properties-window.md)  
 Explique comment exposer les propriétés publiques d’un objet pour le **propriétés** fenêtre.  
  
 [Prise en charge des propriétés de configuration et de projet](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Explique comment afficher et modifier les propriétés de configuration et de projet.  
  
 [Obtention des propriétés d’un projet](../extensibility/getting-project-properties.md)  
 Vous guide à travers les étapes de création d’un VSPackage managé qui affiche les propriétés du projet dans une fenêtre outil.  
  
 [Utilisation de la banque de paramètres](../extensibility/using-the-settings-store.md)  
 Explique le mécanisme de persistance des paramètres Store et comment l’utiliser.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Fournit une orientation générale vers des rubriques qui expliquent comment créer et utiliser des VSPackages.
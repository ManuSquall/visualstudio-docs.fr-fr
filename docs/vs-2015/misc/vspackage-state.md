---
title: État VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62979993"
---
# <a name="vspackage-state"></a>État du VSPackage
De nombreux facteurs déterminent l’ensemble des valeurs persistantes, ou l’État, d’une [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] application.  
  
- Les projets ont des propriétés de projet et de configuration.  
  
- Les solutions ont des propriétés.  
  
- Les paramètres utilisateur déterminent la taille et la position des fenêtres de document, des fenêtres outil, de l’état d’ancrage et des raccourcis clavier.  
  
- Les applications peuvent avoir des options qu’un utilisateur définit.  
  
- Les objets qu’une application crée peuvent avoir leurs propres propriétés.  
  
  Voici quelques-unes des façons dont l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] État d’une application peut être géré :  
  
- Via les pages de propriétés projet et solution.  
  
- À l’aide de l' **Assistant importation et exportation de paramètres**, qui permet à un utilisateur de déplacer des paramètres d’un ordinateur à un autre.  
  
- Via la boîte de dialogue **options** , qui comprend des options relatives aux applications.  
  
- Via la fenêtre **Propriétés** , qui expose les propriétés d’objets.  
  
- Via Automation. Une application peut accéder au VSPackage et aux propriétés des objets qui ont été exposés à Automation.  
  
  Sous-jacent l’état de l’application sont différents mécanismes de persistance qui permettent d’enregistrer et de restaurer l’état de l’application.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge de la persistance de l’état](../misc/support-for-state-persistence.md)  
 Répertorie les stratégies couramment utilisées pour enregistrer, restaurer et réinitialiser l’état d’un VSPackage.  
  
 [Options et pages Options](../extensibility/internals/options-and-options-pages.md)  
 Présente des pages d’options générales et personnalisées et explique comment les implémenter.  
  
 [Création d’une page d’options](../extensibility/creating-an-options-page.md)  
 Explique comment créer deux pages d’options, une page simple et une page personnalisée.  
  
 [Prise en charge des catégories de paramètres](../misc/support-for-settings-categories.md)  
 Décrit les paramètres utilisateur et la façon dont ils sont créés et rendus persistants.  
  
 [Création d’une catégorie de paramètres](../extensibility/creating-a-settings-category.md)  
 Explique comment créer une [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] catégorie de paramètres et l’utiliser pour enregistrer et restaurer des valeurs à partir d’un fichier de paramètres.  
  
 [Extension des propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)  
 Explique comment afficher et modifier la valeur d’un objet dans la fenêtre **Propriétés** .  
  
 [Exposition des propriétés dans la fenêtre Propriétés](../extensibility/exposing-properties-to-the-properties-window.md)  
 Explique comment exposer les propriétés publiques d’un objet dans la fenêtre **Propriétés** .  
  
 [Prise en charge des propriétés de configuration et de projet](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Explique comment afficher et modifier les propriétés de projet et de configuration.  
  
 [Obtention des propriétés d’un projet](../extensibility/getting-project-properties.md)  
 Vous guide tout au long des étapes de création d’un VSPackage géré qui affiche les propriétés d’un projet dans une fenêtre outil.  
  
 [Utilisation de la banque de paramètres](../extensibility/using-the-settings-store.md)  
 Explique le mécanisme de persistance du magasin de paramètres et comment l’utiliser.  
  
## <a name="related-sections"></a>Sections connexes  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Fournit une orientation générale pour les rubriques qui expliquent comment créer et utiliser des VSPackages.
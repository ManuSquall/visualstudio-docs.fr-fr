---
title: Extension de la boîte à outils | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: jillfra
ms.openlocfilehash: 54026b770a0de7780e950a3e30e649cb67ce1d3b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822547"
---
# <a name="extending-the-toolbox"></a>Extension de la boîte à outils
La **boîte à outils** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] propose une collection d’objets qui fournissent des fonctionnalités aux éditeurs et aux concepteurs par le biais du mécanisme glisser-déplacer de l’IDE.  
  
 Il existe deux façons de base dans lequel un VSPackage interagit avec le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **boîte à outils**:  
  
- Un VSPackage peut ajouter de nouveaux contrôles et éléments de données à la **boîte à outils**.  
  
- Un VSPackage, qui peut être la cible ou le consommateur d’une fonctionnalité existante de la **boîte à outils** , prend en charge les opérations de glisser-déplacer et configure l’apparence de la **boîte à outils**.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Créer un contrôle de boîte à outils qui utilise Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Décrit comment créer un contrôle de boîte à outils à l’aide du modèle de contrôle de boîte à outils Windows Forms.  
  
 [Création d’un contrôle de boîte à outils WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 Décrit comment créer un contrôle de boîte à outils à l’aide du modèle de contrôle de boîte à outils WPF.  
  
 [Gestion de la boîte à outils](../misc/managing-the-toolbox.md)  
 Décrit comment un VSPackage peut gérer le contenu et l’apparence de la **boîte à outils**.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Guide pratique pour Gérer la fenêtre Boîte à outils](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Décrit comment utiliser la **boîte à outils** dans l’environnement de développement intégré (IDE) de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Guide pratique pour La boîte à outils de contrôle](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Décrit comment gérer la **boîte à outils** à l’aide du modèle de programmation Automation.  
  
 [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment utiliser les services de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].
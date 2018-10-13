---
title: Extension des Menus et commandes | Microsoft Docs
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
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20ec62586f9a725c1a33da60986d3c8729f0e402
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260999"
---
# <a name="extending-menus-and-commands"></a>Extension des menus et des commandes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les commandes sont la façon que vous ajoutez des actions et les processus dans Visual Studio. Dans la plupart des cas, les commandes sont affichées dans les menus ou barres d’outils. Le modèle de projet VSPackage montre comment implémenter une commande très basique. Pour une implémentation légèrement plus longue mais toujours basique, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Pour plus d’informations sur les commandes de Visual Studio, des menus et barres d’outils, consultez [commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Commandes, menus et barres d’outils sont définis dans le fichier .vsct qui fait partie des projets de VSPackage. Vous trouverez des informations sur l’IDE Visual Studio et le fichier .vsct dans [comment VSPackages ajouter des éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Les rubriques suivantes expliquent comment ajouter différents types de commandes, menus et barres d’outils.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Ajout d’un menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Explique comment ajouter un menu dans la barre de menus Visual Studio.  
  
 [Liaison de raccourcis clavier à des éléments de menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Explique comment ajouter un raccourci clavier (par exemple, CTRL + 3) à un élément de menu.  
  
 [Ajout d’un sous-menu à un menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Explique comment ajouter un sous-menu au menu supérieur.  
  
 [Ajout d’une liste de fichiers récents à un sous-menu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Explique comment ajouter une liste des derniers fichiers utilisés.  
  
 [Création de groupes de boutons réutilisables](../extensibility/creating-reusable-groups-of-buttons.md)  
 Décrit comment regrouper les éléments de commande afin qu’elles peuvent être incluses dans les menus plusieurs.  
  
 [Ajout d’icônes aux commandes de menu](../extensibility/adding-icons-to-menu-commands.md)  
 Décrit comment ajouter une icône à une commande sur une barre d’outils et un menu.  
  
 [Modification du texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Décrit l’utilisation de la `TextChanges` indicateur pour activer un élément de menu être modifié dynamiquement.  
  
 [Modification de l’apparence d’une commande](../extensibility/changing-the-appearance-of-a-command.md)  
 Décrit comment activer ou désactiver une commande de manière dynamique.  
  
 [Mise à jour de l’interface utilisateur](../extensibility/updating-the-user-interface.md)  
 Décrit comment forcer une mise à jour de l’interface utilisateur afin de refléter les modifications récentes.  
  
 [Localisation des commandes de menu](../extensibility/localizing-menu-commands.md)  
 Explique comment localiser les commandes de menu.  
  
## <a name="related-sections"></a>Rubriques connexes


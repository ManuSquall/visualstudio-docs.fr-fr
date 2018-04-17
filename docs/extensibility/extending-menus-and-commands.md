---
title: Extension des Menus et commandes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 830748be6f2cedf57b94a9824bc0912820067718
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="extending-menus-and-commands"></a>Extension des Menus et commandes
Les commandes sont la façon d’ajouter des actions et les processus pour Visual Studio. Dans la plupart des cas, les commandes sont affichées dans les menus ou barres d’outils. Le modèle de projet VSPackage montre comment implémenter une commande très simple. Pour une implémentation légèrement plus longue mais toujours basique, consultez [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Pour plus d’informations sur les commandes de Visual Studio, menus et barres d’outils, consultez [commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Commandes, menus et barres d’outils sont définis dans le fichier .vsct qui fait partie d’un VSPackage projets. Vous trouverez plus d’informations sur l’IDE de Visual Studio et le fichier .vsct dans [comment VSPackages ajouter des éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
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
 Décrit comment regrouper les éléments de la commande afin qu’ils ne peuvent être inclus dans plusieurs menus.  
  
 [Ajout d’icônes aux commandes de menu](../extensibility/adding-icons-to-menu-commands.md)  
 Décrit comment ajouter une icône à une commande sur une barre d’outils et un menu.  
  
 [Modification du texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Décrit l’utilisation de la `TextChanges` indicateur pour activer un élément de menu à être modifiées de manière dynamique.  
  
 [Modification de l’apparence d’une commande](../extensibility/changing-the-appearance-of-a-command.md)  
 Décrit comment activer ou désactiver une commande de manière dynamique.  
  
 [Mise à jour de l’interface utilisateur](../extensibility/updating-the-user-interface.md)  
 Décrit comment forcer une mise à jour de l’interface utilisateur afin de refléter les modifications récentes.  
  
 [Localisation des commandes de menu](../extensibility/localizing-menu-commands.md)  
 Explique comment localiser les commandes de menu.  
  
## <a name="related-sections"></a>Rubriques connexes
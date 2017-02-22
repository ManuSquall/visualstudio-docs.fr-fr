---
title: "Extension des Menus et commandes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menus, des tâches courantes"
  - "VSPackages, menu tâches"
  - "fichiers .vsct, tâches de menu courantes"
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 49
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 49
---
# Extension des Menus et commandes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les commandes sont la manière d'ajouter des actions et les processus pour Visual Studio. Dans la plupart des cas, les commandes sont affichées dans les menus ou barres d'outils. Le modèle de projet VSPackage montre comment implémenter une commande de base. Pour une implémentation légèrement plus longue mais toujours basique, consultez [Création d'une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Pour plus d'informations sur les commandes, les menus et les barres d'outils de Visual Studio, consultez [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Commandes, menus et barres d'outils sont définies dans le fichier .vsct qui fait partie d'un VSPackage projets. Vous trouverez des informations sur l'IDE de Visual Studio et le fichier .vsct dans [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Les rubriques suivantes expliquent comment ajouter différents types de commandes, des menus et barres d'outils.  
  
## Dans cette section  
 [Ajout d'un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Explique comment ajouter un menu dans la barre de menus Visual Studio.  
  
 [Raccourcis clavier de liaison aux éléments de Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Explique comment ajouter un raccourci clavier \(par exemple, CTRL \+ 3\) à un élément de menu.  
  
 [Ajout d'un sous\-menu à un Menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Explique comment ajouter un sous\-menu au menu supérieur.  
  
 [Ajout d'une plus récemment utilisés à un sous\-menu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Explique comment ajouter une liste des derniers fichiers utilisés.  
  
 [Création de groupes de boutons réutilisables](../extensibility/creating-reusable-groups-of-buttons.md)  
 Décrit comment regrouper des éléments de commande afin qu'elles peuvent être incluses dans plusieurs menus.  
  
 [Ajouter des icônes aux commandes de Menu](../extensibility/adding-icons-to-menu-commands.md)  
 Décrit comment ajouter une icône à une commande dans une barre d'outils et un menu.  
  
 [Modification du texte d’une commande de Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Décrit l'utilisation de la `TextChanges` indicateur pour activer un élément de menu Modifier de manière dynamique.  
  
 [Modification de l’apparence d’une commande](../extensibility/changing-the-appearance-of-a-command.md)  
 Décrit comment activer ou désactiver une commande de manière dynamique.  
  
 [Mise à jour de l’Interface utilisateur](../extensibility/updating-the-user-interface.md)  
 Décrit comment forcer une mise à jour de l'interface utilisateur afin de refléter les modifications récentes.  
  
 [Localisation des commandes de Menu](../extensibility/localizing-menu-commands.md)  
 Explique comment localiser les commandes de menu.  
  
## Rubriques connexes
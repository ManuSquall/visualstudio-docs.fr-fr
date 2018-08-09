---
title: Extension des Menus et commandes | Microsoft Docs
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
ms.openlocfilehash: e6f5cd78709c9a4843588188494b4a70f7268742
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639748"
---
# <a name="extend-menus-and-commands"></a>Étendre des menus et commandes
Les commandes sont la façon que vous ajoutez des actions et les processus dans Visual Studio. Dans la plupart des cas, les commandes sont affichées dans les menus ou barres d’outils. Le modèle de projet VSPackage montre comment implémenter une commande très basique. Pour une implémentation légèrement plus longue mais toujours basique, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Pour plus d’informations sur les commandes de Visual Studio, des menus et barres d’outils, consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Commandes, menus et barres d’outils sont définis dans le *.vsct* fichier faisant partie de projets de VSPackage. Vous trouverez des informations sur l’IDE Visual Studio et le *.vsct* fichier [comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Les rubriques suivantes expliquent comment ajouter différents types de commandes, menus et barres d’outils.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Ajouter un menu dans la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Explique comment ajouter un menu dans la barre de menus Visual Studio.  
  
 [Lier des raccourcis clavier aux éléments de menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Explique comment ajouter un raccourci clavier (par exemple, CTRL + 3) à un élément de menu.  
  
 [Ajouter un sous-menu à un menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Explique comment ajouter un sous-menu au menu supérieur.  
  
 [Ajouter qu'une liste à un sous-menu utilisés récemment](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Explique comment ajouter une liste des derniers fichiers utilisés.  
  
 [Créer des groupes de boutons réutilisables](../extensibility/creating-reusable-groups-of-buttons.md)  
 Décrit comment regrouper les éléments de commande afin qu’elles peuvent être incluses dans les menus plusieurs.  
  
 [Ajouter des icônes aux commandes de menu](../extensibility/adding-icons-to-menu-commands.md)  
 Décrit comment ajouter une icône à une commande sur une barre d’outils et un menu.  
  
 [Modifier le texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Décrit l’utilisation de la `TextChanges` indicateur pour activer un élément de menu être modifié dynamiquement.  
  
 [Modifier l’apparence d’une commande](../extensibility/changing-the-appearance-of-a-command.md)  
 Décrit comment activer ou désactiver une commande de manière dynamique.  
  
 [Mettre à jour de l’interface utilisateur](../extensibility/updating-the-user-interface.md)  
 Décrit comment forcer une mise à jour de l’interface utilisateur afin de refléter les modifications récentes.  
  
 [Localiser des commandes de menu](../extensibility/localizing-menu-commands.md)  
 Explique comment localiser les commandes de menu.  
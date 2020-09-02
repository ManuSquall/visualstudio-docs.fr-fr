---
title: Extension des menus et des commandes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83d9dc45863f1ed1b5e11c17b9e922b62b0186dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204532"
---
# <a name="extending-menus-and-commands"></a>Extension des menus et des commandes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les commandes vous permettent d’ajouter des actions et des processus à Visual Studio. Dans la plupart des cas, les commandes sont affichées dans les menus ou les barres d’outils. Le modèle de projet VSPackage montre comment implémenter une commande de base. Pour une implémentation légèrement plus longue mais toujours de base, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Pour plus d’informations sur les commandes, menus et barres d’outils de Visual Studio, consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Les commandes, les menus et les barres d’outils sont définis dans le fichier. vsct qui fait partie des projets VSPackage. Vous pouvez trouver des informations sur l’IDE de Visual Studio et le fichier. vsct dans la [manière dont les VSPackages ajoutent des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Les rubriques suivantes expliquent comment ajouter différents types de commandes, de menus et de barres d’outils.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Ajout d’un menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Explique comment ajouter un menu à la barre de menus supérieure de Visual Studio.  
  
 [Liaison de raccourcis clavier à des éléments de menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Explique comment ajouter un raccourci clavier (tel que CTRL + 3) à un élément de menu.  
  
 [Ajout d’un sous-menu à un menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Explique comment ajouter un sous-menu au menu supérieur.  
  
 [Ajout d’une liste de fichiers récents à un sous-menu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Explique comment ajouter une liste des derniers fichiers utilisés.  
  
 [Création de groupes de boutons réutilisables](../extensibility/creating-reusable-groups-of-buttons.md)  
 Décrit comment regrouper des éléments de commande afin qu’ils puissent être inclus dans plusieurs menus.  
  
 [Ajout d’icônes aux commandes de menu](../extensibility/adding-icons-to-menu-commands.md)  
 Décrit comment ajouter une icône à une commande à la fois dans une barre d’outils et dans un menu.  
  
 [Modification du texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Décrit l’utilisation de l' `TextChanges` indicateur pour permettre la modification dynamique d’un élément de menu.  
  
 [Modification de l’apparence d’une commande](../extensibility/changing-the-appearance-of-a-command.md)  
 Décrit comment activer ou désactiver dynamiquement une commande.  
  
 [Mise à jour de l'interface utilisateur](../extensibility/updating-the-user-interface.md)  
 Décrit comment forcer une mise à jour de l’interface utilisateur pour refléter les modifications récentes.  
  
 [Localisation des commandes de menu](../extensibility/localizing-menu-commands.md)  
 Explique comment localiser les commandes de menu.  
  
## <a name="related-sections"></a>Sections connexes

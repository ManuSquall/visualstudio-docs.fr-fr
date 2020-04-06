---
title: Extension des menus et des commandes Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711798"
---
# <a name="extend-menus-and-commands"></a>Étendre les menus et les commandes
Les commandes sont la façon dont vous ajoutez des actions et des processus à Visual Studio. Dans la plupart des cas, les commandes sont affichées sur les menus ou les barres d’outils. Le modèle de projet VSPackage montre comment implémenter une commande très basique. Pour une implémentation légèrement plus longue mais toujours de base, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

 Pour plus d’informations sur les commandes Visual Studio, les menus et les barres d’outils, voir [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

 Les commandes, les menus et les barres d’outils sont définis dans le fichier *.vsct* qui fait partie des projets VSPackage. Vous pouvez trouver des informations sur l’IDE Visual Studio et le fichier *.vsct* dans [Comment VSPackages ajouter des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Les sujets suivants expliquent comment ajouter différents types de commandes, de menus et de barres d’outils.

## <a name="in-this-section"></a>Contenu de cette section
- [Ajoutez un menu au menu Visual Studio bar](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Explique comment ajouter un menu au menu Visual Studio haut.

- [Lier les raccourcis clavier aux éléments du menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Explique comment ajouter un raccourci clavier (comme CTRL 3) à un élément de menu.

- [Ajouter un sous-mois à un menu](../extensibility/adding-a-submenu-to-a-menu.md) Explique comment ajouter un sous-mois au menu supérieur.

- [Ajouter une liste plus récemment utilisée à un sous-mois](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Explique comment ajouter une liste la plus récemment utilisée.

- [Créer des groupes réutilisables de boutons](../extensibility/creating-reusable-groups-of-buttons.md) Décrit comment regrouper les articles de commande afin qu’ils puissent être inclus sur plusieurs menus.

- [Ajouter des icônes aux commandes de menu](../extensibility/adding-icons-to-menu-commands.md) Décrit comment ajouter une icône à une commande à la fois sur une barre d’outils et un menu.

- [Modifier le texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md) Décrit l’utilisation `TextChanges` du drapeau pour permettre de modifier dynamiquement un élément de menu.

- [Modifier l’apparence d’une commande](../extensibility/changing-the-appearance-of-a-command.md) Décrit comment activer ou désactiver dynamiquement une commande.

- [Mettre à jour l’interface utilisateur](../extensibility/updating-the-user-interface.md) Décrit comment forcer une mise à jour de l’interface utilisateur à refléter les changements récents.

- [Localiser les commandes de menu](../extensibility/localizing-menu-commands.md) Explique comment localiser les commandes de menu.

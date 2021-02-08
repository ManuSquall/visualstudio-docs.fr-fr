---
title: Extension des menus et des commandes | Microsoft Docs
description: En savoir plus sur les commandes, qui ajoutent des actions et des processus à Visual Studio. Le modèle de projet VSPackage montre comment implémenter une commande de base.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4466a180923c85461ede59102b346caf70fd064b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842190"
---
# <a name="extend-menus-and-commands"></a>Étendre des menus et des commandes
Les commandes vous permettent d’ajouter des actions et des processus à Visual Studio. Dans la plupart des cas, les commandes sont affichées dans les menus ou les barres d’outils. Le modèle de projet VSPackage montre comment implémenter une commande de base. Pour une implémentation légèrement plus longue mais toujours de base, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

 Pour plus d’informations sur les commandes, les menus et les barres d’outils de Visual Studio, consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

 Les commandes, les menus et les barres d’outils sont définis dans le fichier *. vsct* qui fait partie des projets VSPackage. Vous pouvez trouver des informations sur l’IDE de Visual Studio et le fichier *. vsct* dans la [manière dont les VSPackages ajoutent des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Les rubriques suivantes expliquent comment ajouter différents types de commandes, de menus et de barres d’outils.

## <a name="in-this-section"></a>Dans cette section
- [Ajouter un menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Explique comment ajouter un menu à la barre de menus supérieure de Visual Studio.

- [Lier des raccourcis clavier à des éléments de menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Explique comment ajouter un raccourci clavier (tel que CTRL + 3) à un élément de menu.

- [Ajouter un sous-menu à un menu](../extensibility/adding-a-submenu-to-a-menu.md) Explique comment ajouter un sous-menu au menu supérieur.

- [Ajouter une liste des derniers fichiers utilisés à un sous-menu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Explique comment ajouter une liste des derniers fichiers utilisés.

- [Créer des groupes de boutons réutilisables](../extensibility/creating-reusable-groups-of-buttons.md) Décrit comment regrouper des éléments de commande afin qu’ils puissent être inclus dans plusieurs menus.

- [Ajouter des icônes aux commandes de menu](../extensibility/adding-icons-to-menu-commands.md) Décrit comment ajouter une icône à une commande à la fois dans une barre d’outils et dans un menu.

- [Modifier le texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md) Décrit l’utilisation de l' `TextChanges` indicateur pour permettre la modification dynamique d’un élément de menu.

- [Modifier l’apparence d’une commande](../extensibility/changing-the-appearance-of-a-command.md) Décrit comment activer ou désactiver dynamiquement une commande.

- [Mettre à jour l’interface utilisateur](../extensibility/updating-the-user-interface.md) Décrit comment forcer une mise à jour de l’interface utilisateur pour refléter les modifications récentes.

- [Localiser les commandes de menu](../extensibility/localizing-menu-commands.md) Explique comment localiser les commandes de menu.

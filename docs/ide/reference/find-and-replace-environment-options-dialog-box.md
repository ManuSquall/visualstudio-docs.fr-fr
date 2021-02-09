---
title: Rechercher et remplacer, Environnement, boîte de dialogue Options
description: Découvrez comment utiliser la page Rechercher et remplacer dans la section environnement pour contrôler les boîtes de message et d’autres aspects d’une opération de recherche et de remplacement.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.FindReplace
- VS.ToolsOptionsPages.Environment.FindandReplace
helpviewer_keywords:
- Find and Replace, Options dialog box
- Find and Replace, customizing
ms.assetid: f804d6d5-6309-46e4-8294-b83e880b5ec9
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0fab4fd10d985ad1cee01fbea4269934c01d243
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860917"
---
# <a name="find-and-replace-environment-options-dialog-box"></a>Rechercher et remplacer, Environnement, boîte de dialogue Options

Utilisez cette page de la boîte de dialogue **Options** pour contrôler les boîtes de message et d’autres aspects d’une opération de recherche et de remplacement. Vous pouvez accéder à cette boîte de dialogue à partir du menu **Outils** en cliquant sur **Options**, en développant **Environnement**, puis en cliquant sur **Rechercher et remplacer**. Si cette page n’apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

**Afficher des messages d’information**

Sélectionnez cette option pour afficher tous les messages d’information Rechercher et remplacer dotés de l’option **Toujours afficher ce message**. Par exemple, si vous avez choisi de ne pas afficher le message « Le début de la recherche est atteint. », sélectionner cette option provoquerait de nouveau l’affichage de ce message d’information lorsque vous utilisez Rechercher et remplacer.

Si vous ne souhaitez pas voir de messages d’information pour la fonctionnalité Rechercher et remplacer, désactivez cette option.

Si vous avez désactivé l’option **Toujours afficher ce message** pour certains messages d’information **Rechercher et remplacer** mais pas tous, la case à cocher **Afficher des messages d’information** apparaît remplie mais pas sélectionnée. Pour restaurer tous les messages **Rechercher et remplacer** facultatifs, désactivez cette option, puis sélectionnez-la de nouveau.

> [!NOTE]
> Cette option n’affecte pas les messages d’information **Rechercher et remplacer** qui ne présentent pas l’option **Toujours afficher ce message**.

**Afficher des messages d’avertissement**

Sélectionnez cette option pour afficher tous les messages d’avertissement Rechercher et remplacer dotés de l’option **Toujours afficher ce message**. Par exemple, si vous avez choisi de ne pas afficher le message d’avertissement **Remplacer tout** qui s’affiche lorsque vous essayez d’effectuer des remplacements dans des fichiers qui ne sont pas ouverts pour modification, cette option entraîne de nouveau l’affichage de ce message d’avertissement si vous tentez de tout remplacer.

Si vous ne souhaitez pas voir de messages d’avertissement pour la fonctionnalité Rechercher et remplacer, désactivez cette option.

Si vous avez désactivé l’option **Toujours afficher ce message** pour certains messages d’avertissement **Rechercher et remplacer** mais pas tous, la case à cocher **Afficher des messages d’avertissement** apparaît remplie mais pas sélectionnée. Pour restaurer tous les messages **Rechercher et remplacer** facultatifs, désactivez cette option, puis sélectionnez-la de nouveau.

> [!NOTE]
> Cette option n’affecte pas les messages d’avertissement **Rechercher et remplacer** qui ne présentent pas l’option **Toujours afficher ce message**.

**Remplir automatiquement la zone Rechercher à l’aide du texte de l’éditeur**

Sélectionnez cette option pour coller le texte de chaque côté du point d’insertion de l’éditeur actuel dans le champ **Rechercher** lorsque vous sélectionnez n’importe quelle vue de la fenêtre **Rechercher et remplacer** à partir du menu **Edition**. Désactivez cette option pour utiliser le dernier modèle de recherche utilisé à la recherche précédente comme chaîne **Rechercher**.

## <a name="see-also"></a>Voir aussi

- [Recherche et remplacement de texte](../../ide/finding-and-replacing-text.md)

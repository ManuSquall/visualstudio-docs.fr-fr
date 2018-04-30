---
title: Guide pratique pour créer et modifier des configurations
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3aa3aaa197f392d300e8787d582314846e789f47
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-and-edit-configurations"></a>Guide pratique pour créer et modifier des configurations

Vous pouvez créer plusieurs configurations de build pour une solution. Par exemple, vous pouvez configurer une build de débogage que vos testeurs peuvent utiliser pour rechercher et résoudre des problèmes. Vous pouvez également configurer différents types de builds que vous pouvez distribuer à des clients différents.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-build-configurations"></a>Créer des configurations de build

Vous pouvez utiliser la boîte de dialogue **Gestionnaire de configurations** pour sélectionner ou modifier des configurations de build existantes, ou en créer d’autres.

Pour ouvrir la boîte de dialogue **Gestionnaire de configurations**, dans l’**Explorateur de solutions**, ouvrez le menu contextuel de la solution, puis choisissez **Gestionnaire de configurations**.

> [!NOTE]
> Si la commande **Gestionnaire de configurations** n’apparaît pas dans le menu contextuel, regardez sous le menu **Générer**, dans la barre de menus. Si elle n’y figure pas non plus, dans la barre de menus, choisissez **Outils** > **Options**. Dans le volet gauche de la boîte de dialogue **Options**, développez **Projets et solutions** > **Général**, puis dans le volet droit, cochez la case **Afficher les configurations de build avancées**.

Dans la boîte de dialogue **Gestionnaire de configurations**, vous pouvez utiliser la liste déroulante **Configuration de la solution active** pour sélectionner une configuration de build à l’échelle de la solution, modifier une configuration existante ou créer une nouvelle configuration. Vous pouvez utiliser la liste déroulante **Plateforme de la solution active** pour sélectionner la plateforme ciblée par la configuration, modifier une plateforme existante ou ajouter une nouvelle plateforme. Le volet **Contextes des projets** répertorie les projets de la solution. Pour chaque projet, vous pouvez sélectionner une plateforme et une configuration spécifiques au projet, modifier celles existantes, ou créer une nouvelle configuration et ajouter une nouvelle plateforme. Vous pouvez également cocher les cases qui indiquent si chaque projet est inclus lorsque vous utilisez la configuration à l’échelle de la solution pour générer ou déployer la solution.

 Après avoir installé les configurations de votre choix, vous pouvez définir les propriétés de projet appropriées pour ces configurations.

### <a name="to-set-properties-based-on-configurations"></a>Pour définir des propriétés sur la base de configurations

-   Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel d’un projet et choisissez **Propriétés**.

     La fenêtre **Pages de propriétés** apparaît.

     Vous pouvez définir des propriétés pour vos configurations. Par exemple, pour une configuration Release, vous pouvez spécifier l’optimisation du code quand la solution est générée et, pour une configuration Debug, vous pouvez spécifier l’ajout du symbole de compilation conditionnelle `DEBUG`. Pour plus d’informations sur les paramètres des pages de propriétés, consultez [Gestion des propriétés des projets et des solutions](../ide/managing-project-and-solution-properties.md).

## <a name="create-and-modify-project-configurations"></a>Créer et modifier des configurations de projet

### <a name="to-create-a-project-configuration"></a>Pour créer une configuration de projet

1.  Ouvrez la boîte de dialogue **Gestionnaire de configurations**.

2.  Sélectionnez un projet dans la colonne **Projet**.

3.  Dans la liste déroulante **Configuration** de ce projet, choisissez **Nouveau**.

     La boîte de dialogue **Nouvelle configuration de projet** apparaît.

4.  Dans la zone **Nom**, entrez un nom pour la nouvelle configuration.

5.  Pour utiliser les paramètres de propriété d’une configuration de projet existante, dans la liste déroulante **Copier les paramètres à partir de**, choisissez une configuration.

6.  Pour créer une configuration à l’échelle de la solution au même moment, cochez la case **Créer une nouvelle configuration de solution**.

### <a name="to-rename-a-project-configuration"></a>Pour renommer une configuration de projet

1.  Ouvrez la boîte de dialogue **Gestionnaire de configurations**.

2.  Dans la colonne **Projet**, sélectionnez le projet dont vous souhaitez renommer la configuration de projet.

3.  Dans la liste déroulante **Configuration** de ce projet, choisissez **Modifier**.

     La boîte de dialogue **Modifier les configurations de projet** apparaît.

4.  Sélectionnez le nom de la configuration de projet à modifier.

5.  Sélectionnez **Renommer**, puis entrez un nouveau nom.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Créer et modifier des configurations de build à l’échelle de la solution

### <a name="to-create-a-solution-wide-build-configuration"></a>Pour créer une configuration de build à l’échelle de la solution

1.  Ouvrez la boîte de dialogue **Gestionnaire de configurations**.

2.  Dans la liste déroulante **Configuration de la solution active**, choisissez **Nouveau**.

     La boîte de dialogue **Nouvelle configuration de solution** apparaît.

3.  Dans la zone de texte **Nom**, entrez un nom pour la nouvelle configuration.

4.  Pour utiliser les paramètres d’une configuration de solution existante, dans la liste déroulante **Copier les paramètres à partir de**, choisissez une configuration.

5.  Si vous souhaitez créer des configurations de projet au même moment, cochez la case **Créer des configurations de projet**.

### <a name="to-rename-a-solution-wide-build-configuration"></a>Pour renommer une configuration de build à l’échelle de la solution

1.  Ouvrez la boîte de dialogue **Gestionnaire de configurations**.

2.  Dans la liste déroulante **Configuration de la solution active**, choisissez **Modifier**.

     La boîte de dialogue **Modifier les configurations de solutions** apparaît.

3.  Sélectionnez le nom de la configuration de solution à modifier.

4.  Sélectionnez **Renommer**, puis entrez un nouveau nom.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Pour modifier une configuration de build à l’échelle de la solution

1.  Ouvrez la boîte de dialogue **Gestionnaire de configurations**.

2.  Dans la liste déroulante **Configuration de la solution active**, sélectionnez la configuration de votre choix.

3.  Dans le volet **Contextes des projets**, pour chaque projet, sélectionnez la **Configuration** et la **Plateforme** de votre choix, puis choisissez entre **Générer** ou **Déployer**.

## <a name="see-also"></a>Voir aussi

- [Présentation des configurations de build](../ide/understanding-build-configurations.md)
- [Générer et nettoyer des solutions et des projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Gérer les propriétés des projets et des solutions](managing-project-and-solution-properties.md)
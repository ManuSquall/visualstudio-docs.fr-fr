---
title: Utilisation des ensembles de règles pour spécifier les règles C++ à exécuter
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 571d54bb6bdf3673da8e40d6075c5b961d248fe5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Utiliser des ensembles de règles pour spécifier les règles C++ à exécuter

Dans Visual Studio, vous pouvez créer et modifier une personnalisée *ensemble de règles* pour répondre aux besoins de projet spécifique associés à l’analyse du code. Pour créer une règle C++ personnalisée configuré, un projet C/C++ doit être ouvert dans l’IDE de Visual Studio. Vous puis ouvrez un ensemble de règles standard dans l’éditeur d’ensemble de règles et puis ajoutez ou supprimez des règles spécifiques et éventuellement modifiez l’action qui se produit lorsque l’analyse du code détermine qu’une règle a été violée.

Pour créer une nouvelle règle personnalisée définie, vous l’enregistrez à l’aide d’un nouveau nom de fichier. L’ensemble de règles personnalisé est automatiquement attribué au projet.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Pour créer une règle personnalisée à partir d’un seul ensemble de règles existant

1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du projet, puis choisissez **propriétés**.

2. Sur le **propriétés** , onglet choisir **l’analyse du Code**.

3. Dans le **l’ensemble de règles** liste déroulante, effectuez l’une des opérations suivantes :

    - Choisissez l’ensemble de règles que vous souhaitez personnaliser.

     \- ou -

    - Choisissez  **\<Parcourir... >** pour spécifier une règle existante du jeu qui n’est pas dans la liste.

4. Choisissez **ouvrir** pour afficher les règles dans l’éditeur d’ensemble de règles.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Pour modifier une règle définie dans l’éditeur d’ensemble de règles

- Pour modifier le nom complet de l’ensemble de règles, dans le **vue** menu, choisissez **fenêtre Propriétés**. Entrez le nom d’affichage dans le **nom** boîte. Notez que le nom complet peut différer du nom de fichier.

- Pour ajouter toutes les règles du groupe à un ensemble de règles personnalisé, sélectionnez la case à cocher du groupe. Pour supprimer toutes les règles du groupe, désactivez la case à cocher.

- Pour ajouter une règle spécifique à l’ensemble de règles personnalisé, sélectionnez la case à cocher de la règle. Pour supprimer la règle de l’ensemble de règles, désactivez la case à cocher.

- Pour modifier l’action effectuée lorsqu’une règle est violée dans une analyse du code, choisissez la **Action** champ pour la règle, puis choisissez une des valeurs suivantes :

     **Avertir** -génère un avertissement.

     **Erreur** -génère une erreur.

     **Aucun** -désactive la règle. Cette action est le même que la suppression de la règle de l’ensemble de règles.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Pour regrouper, filtrer ou modifier les champs dans l’éditeur d’ensemble de règles à l’aide de la barre d’outils Éditeur de règle ensemble

- Pour développer les règles dans tous les groupes, choisissez **développer tout**.

- Pour réduire les règles dans tous les groupes, choisissez **réduire tout**.

- Pour modifier le champ règles sont regroupées, choisissez le champ à partir de la **Group By** liste. Pour afficher les règles non groupés, choisissez  **\<aucun >**.

- Pour ajouter ou supprimer des champs dans les colonnes de la règle, choisissez **Options de colonne**.

- Pour masquer les règles qui ne s’appliquent pas à la solution actuelle, choisissez **masquer des règles qui ne s’appliquent pas à la solution actuelle**.

- Pour basculer entre l’affichage et masquage des règles qui sont affectés à l’action d’erreur, choisissez **afficher les règles qui peuvent générer des erreurs d’analyse du Code**.

- Pour basculer entre l’affichage et masquage des règles qui sont affectés à l’action de l’avertissement, choisissez **afficher les règles qui peuvent générer des avertissements d’analyse du Code**.

- Pour basculer entre l’affichage et masquage des règles qui sont affectés les **aucun** action, choisissez **afficher les règles qui ne sont pas activées**.

- Pour ajouter ou supprimer des ensembles de règle par défaut pour l’ensemble de règles actuel Microsoft, choisissez **des ensembles de règles enfants Add ou remove**.
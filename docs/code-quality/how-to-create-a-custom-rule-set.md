---
title: Créer une règle d’analyse de code personnalisé définie dans Visual Studio | Documents Microsoft
ms.date: 04/04/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57800f36c3a81e021c1fb40bab1c07bbed3e7f9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="custom-rule-sets"></a>Ensembles de règles personnalisés

Vous pouvez créer un *ensemble de règles* pour répondre aux besoins de projet spécifiques pour l’analyse du code.

## <a name="create-a-custom-rule-set"></a>Créer un ensemble de règles personnalisé

Pour créer une règle personnalisée définie, vous pouvez ouvrir une règle intégrée définie dans le **Éditeur d’ensemble de règles**. À partir de là, vous pouvez ajouter ou supprimer des règles spécifiques, et vous pouvez modifier l’action qui se produit lorsqu’une règle est violée&mdash;, par exemple, afficher un avertissement ou une erreur.

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis sélectionnez **propriétés**.

2. Sur le **propriétés** pages, sélectionnez le **l’analyse du Code** onglet.

3. Dans le **exécuter cet ensemble de règles** liste déroulante, effectuez l’une des opérations suivantes :

    - Sélectionnez l’ensemble de règles que vous souhaitez personnaliser.

     \- ou -

    - Sélectionnez  **\<Parcourir... >** pour spécifier une règle existante du jeu qui n’est pas dans la liste.

4. Sélectionnez **ouvrir** pour afficher les règles dans l’éditeur d’ensemble de règles.

Vous pouvez également créer un nouveau fichier de jeu de règles à partir de la **nouveau fichier** boîte de dialogue :

1. Sélectionnez **fichier** > **nouveau** > **fichier**, ou appuyez sur **Ctrl**+**N**.

2. Dans le **nouveau fichier** boîte de dialogue, sélectionnez le **général** catégorie sur la gauche, puis sélectionnez **ensemble de règles d’analyse de Code**.

3. Sélectionnez **Ouvrir**.

   La nouvelle *.ruleset* fichier s’ouvre dans l’éditeur d’ensemble de règles.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Créer une règle personnalisée définie à partir de plusieurs ensembles de règles

1. Dans l’Explorateur de solutions, cliquez sur le projet, puis sélectionnez **propriétés**.

2. Sur le **propriétés** pages, sélectionnez le **l’analyse du Code** onglet.

3. Sélectionnez  **\<choisir plusieurs règle définit... >** de **exécuter cet ensemble de règles**.

4. Dans le **ajouter ou supprimer des ensembles de règles** boîte de dialogue, sélectionnez les ensembles de règles vous souhaitez inclure dans votre nouvel ensemble de règles.

   ![Ajouter ou supprimer la boîte de dialogue de jeux de règles](media/add-remove-rule-sets.png)

5. Sélectionnez **enregistrer en tant que**, entrez un nom pour le *.ruleset* de fichiers, puis sélectionnez **enregistrer**.

   Nouvel ensemble de règles est sélectionné dans le **exécuter cet ensemble de règles** liste.

6. Sélectionnez **ouvrir** pour ouvrir la nouvelle règle, définie dans l’éditeur d’ensemble de règles.

## <a name="name-and-description"></a>Nom et description

Pour modifier le nom complet d’un ensemble de règles est ouvert dans l’éditeur, ouvrez le **propriétés** en sélectionnant **vue** > **fenêtre Propriétés** sur la barre de menus. Entrez le nom d’affichage dans le **nom** boîte. Vous pouvez également entrer une description pour l’ensemble de règles.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez une règle définie, l’étape suivante consiste à personnaliser les règles en ajoutant ou supprimant des règles ou modifier le niveau de gravité des violations de règles.

> [!div class="nextstepaction"]
> [Modifier les règles dans l’éditeur d’ensemble de règles](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour configurer l’analyse du code pour un projet de code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Informations de référence sur l’ensemble de règles d’analyse du code](../code-quality/rule-set-reference.md)
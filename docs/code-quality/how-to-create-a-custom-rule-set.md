---
title: Créer un ensemble de règles d’analyse code personnalisé
ms.date: 11/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2f642ea8e41e4a9ccf2b35f432df528fc5e81d0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676565"
---
# <a name="customize-a-rule-set"></a>Personnaliser un ensemble de règles

Vous pouvez créer une règle personnalisée définie pour répondre aux besoins de projet spécifiques pour l’analyse du code.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Créer une règle personnalisée définie à partir d’un ensemble de règles existant

Pour créer une règle personnalisée, vous pouvez ouvrir un intégrés ensemble de règles dans le **Éditeur d’ensemble de règles**. À partir de là, vous pouvez ajouter ou supprimer des règles spécifiques, et vous pouvez modifier l’action qui se produit lorsqu’une règle est violée&mdash;, par exemple, afficher un avertissement ou une erreur.

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis sélectionnez **propriétés**.

2. Sur le **propriétés** pages, sélectionnez le **analyse du Code** onglet.

3. Dans le **exécuter cet ensemble de règles** liste déroulante, effectuez l’une des opérations suivantes :

   - Sélectionnez l’ensemble de règles que vous souhaitez personnaliser.

     \- ou -

   - Sélectionnez  **\<Parcourir... >** pour spécifier une règle existante définie qui n’est pas dans la liste.

4. Sélectionnez **Open** pour afficher les règles dans l’éditeur d’ensemble de règles.

> [!NOTE]
> Si vous avez un projet .NET Core ou .NET Standard, le processus est un peu différent, car il n’est pas **analyse du Code** onglet de propriété. Suivez les étapes pour [copier une règle prédéfinie défini à votre projet et définissez-le comme l’ensemble de règles active](analyzer-rule-sets.md). Une fois que vous avez copié sur un ensemble de règles, vous pouvez [modifier dans l’éditeur d’ensemble de règles de Visual Studio](working-in-the-code-analysis-rule-set-editor.md) en l’ouvrant à partir de **l’Explorateur de solutions**.

## <a name="create-a-new-rule-set"></a>Créer un ensemble de règles

Vous pouvez créer un nouveau fichier de jeu de règles à partir de la **nouveau fichier** boîte de dialogue :

1. Sélectionnez **fichier** > **New** > **fichier**, ou appuyez sur **Ctrl**+**N**.

2. Dans le **nouveau fichier** boîte de dialogue, sélectionnez le **général** catégorie sur la gauche, puis sélectionnez **ensemble de règles d’analyse de Code**.

3. Sélectionnez **Ouvrir**.

   La nouvelle *.ruleset* fichier s’ouvre dans l’éditeur d’ensemble de règles.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Créer une règle personnalisée définie à partir de plusieurs ensembles de règles

> [!NOTE]
> La procédure suivante ne s’applique pas aux projets .NET Core, qui n’ont pas un **analyse du Code** onglet de propriété.

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis sélectionnez **propriétés**.

2. Sur le **propriétés** pages, sélectionnez le **analyse du Code** onglet.

3. Sélectionnez  **\<choisir plusieurs règle définit... >** de **exécuter cet ensemble de règles**.

4. Dans le **ajouter ou supprimer des ensembles de règles** boîte de dialogue, sélectionnez les ensembles de règles vous voulez inclure dans un ensemble de règles.

   ![Ajouter ou supprimer la boîte de dialogue de jeux de règles](media/add-remove-rule-sets.png)

5. Sélectionnez **enregistrer en tant que**, entrez un nom pour le *.ruleset* de fichiers, puis sélectionnez **enregistrer**.

   Nouvel ensemble de règles est sélectionné dans le **exécuter cet ensemble de règles** liste.

6. Sélectionnez **ouvrir** pour ouvrir la nouvelle règle définie dans l’éditeur d’ensemble de règles.

## <a name="rule-precedence"></a>Priorité des règles

- Si la même règle est répertorié deux fois ou plus dans un jeu de règles par différents niveaux de gravité, le compilateur génère une erreur. Exemple :

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Si la même règle est répertorié deux fois ou plus dans un jeu de règles par le *même* gravité, vous pouvez voir l’avertissement suivant dans le **liste d’erreurs**:

   **CA0063 : Échec du chargement du fichier d’ensemble de règles '\[votre] .ruleset ' ou un de ses règles dépendants les fichiers d’ensembles. Le fichier n’est pas conforme au schéma du jeu de règle.**

- Si l’ensemble de règles inclut un ensemble à l’aide de règles enfant un **Include** balise et les ensembles de règles enfants et parents ont tous deux la même règle de liste, mais avec différents niveaux de gravité, puis le niveau de gravité dans l’ensemble de règles parent est prioritaire. Exemple :

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>Nom et description

Pour modifier le nom complet d’un ensemble de règles est ouvert dans l’éditeur, ouvrez le **propriétés** en sélectionnant **vue** > **fenêtre Propriétés** sur la barre de menus. Entrez le nom d’affichage dans le **nom** boîte. Vous pouvez également entrer une description pour l’ensemble de règles.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez une règle définie, l’étape suivante consiste à personnaliser les règles en ajoutant ou supprimant des règles ou en modifiant le niveau de gravité des violations de règle.

> [!div class="nextstepaction"]
> [Modifier les règles dans l’éditeur d’ensemble de règles](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Configurer l’analyse du Code pour un projet de Code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Informations de référence sur l’ensemble de règles d’analyse du code](../code-quality/rule-set-reference.md)
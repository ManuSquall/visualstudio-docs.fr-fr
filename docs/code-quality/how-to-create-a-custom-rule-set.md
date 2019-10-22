---
title: Créer un ensemble de règles d’analyse du code personnalisé
ms.date: 11/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b904fd484135943228b2d8ac21e2df0d1c02e34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649510"
---
# <a name="customize-a-rule-set"></a>Personnaliser un ensemble de règles

Vous pouvez créer un ensemble de règles personnalisé pour répondre à des besoins spécifiques du projet pour l’analyse du code.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Créer un ensemble de règles personnalisé à partir d’un ensemble de règles existant

Pour créer un ensemble de règles personnalisé, vous pouvez ouvrir un ensemble de règles intégré dans l' **éditeur d’ensembles de règles**. À partir de là, vous pouvez ajouter ou supprimer des règles spécifiques, et vous pouvez modifier l’action qui se produit lorsqu’une règle est violée &mdash;for exemple, afficher un avertissement ou une erreur.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.

2. Dans les pages **Propriétés** , sélectionnez l’onglet **analyse du code** .

::: moniker range="vs-2017"

3. Dans la liste déroulante **exécuter cet ensemble de règles** , effectuez l’une des opérations suivantes :

::: moniker-end

::: moniker range=">=vs-2019"

3. Dans la liste déroulante **règles actives** , effectuez l’une des opérations suivantes :

::: moniker-end

   - Sélectionnez l’ensemble de règles que vous souhaitez personnaliser.

     \- ou -

   - Sélectionnez **\<Browse >** pour spécifier un ensemble de règles existant qui ne figure pas dans la liste.

4. Sélectionnez **ouvrir** pour afficher les règles dans l’éditeur d’ensembles de règles.

> [!NOTE]
> Si vous avez un projet .NET Core ou .NET Standard, le processus est un peu différent, car il n’existe pas d’onglet de propriété **analyse du code** . Suivez les étapes pour [copier un ensemble de règles prédéfini vers votre projet et le définir comme l’ensemble de règles actif](analyzer-rule-sets.md). Une fois que vous avez copié un ensemble de règles, vous pouvez [le modifier dans l’éditeur d’ensembles de règles de Visual Studio](working-in-the-code-analysis-rule-set-editor.md) en l’ouvrant à partir de **Explorateur de solutions**.

## <a name="create-a-new-rule-set"></a>Créer un ensemble de règles

Vous pouvez créer un nouveau fichier d’ensemble de règles à partir de la boîte de dialogue **nouveau fichier** :

1. Sélectionnez **fichier** > **nouveau** **fichier** >  ou appuyez sur **CTRL**+**N**.

2. Dans la boîte de dialogue **nouveau fichier** , sélectionnez la catégorie **général** sur la gauche, puis sélectionnez **ensemble de règles d’analyse du code**.

3. Sélectionnez **Ouvrir**.

   Le nouveau fichier *. RuleSet* s’ouvre dans l’éditeur d’ensembles de règles.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Créer un ensemble de règles personnalisé à partir de plusieurs ensembles de règles

> [!NOTE]
> La procédure suivante ne s’applique pas aux projets .NET Core, qui n’ont pas d’onglet de propriété **analyse du code** .

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.

2. Dans les pages **Propriétés** , sélectionnez l’onglet **analyse du code** .

::: moniker range="vs-2017"

3. Sélectionnez **\<Choose plusieurs ensembles de règles >** à partir de **exécuter cet ensemble de règles**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Sélectionnez **\<Choose plusieurs ensembles de règles >** à partir des **règles actives**.

::: moniker-end

4. Dans la boîte de dialogue **Ajouter ou supprimer des ensembles de règles** , sélectionnez les ensembles de règles que vous souhaitez inclure dans votre nouvel ensemble de règles.

   ![Boîte de dialogue Ajouter ou supprimer des ensembles de règles](media/add-remove-rule-sets.png)

5. Sélectionnez **Enregistrer sous**, entrez un nom pour le fichier *. RuleSet* , puis sélectionnez **Enregistrer**.

   Le nouvel ensemble de règles est sélectionné dans la liste **exécuter cet ensemble de règles** .

6. Sélectionnez **ouvrir** pour ouvrir le nouvel ensemble de règles dans l’éditeur d’ensembles de règles.

## <a name="rule-precedence"></a>Priorité des règles

- Si la même règle est listée deux fois ou plus dans un ensemble de règles avec des gravités différentes, le compilateur génère une erreur. Exemple :

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Si la même règle est listée deux fois ou plus dans un ensemble de règles avec la *même* gravité, l’avertissement suivant peut s’afficher dans la **liste d’erreurs**:

   **CA0063 : échec du chargement du fichier d’ensemble de règles' \[your]. RuleSet’ou de l’un de ses fichiers d’ensemble de règles dépendants. Le fichier n’est pas conforme au schéma de l’ensemble de règles.**

- Si l’ensemble de règles inclut un ensemble de règles enfant à l’aide d’une balise **include** , et que la règle enfant et parent affecte à la fois la même règle, mais avec des niveaux de gravité différents, la gravité de l’ensemble de règles parent est prioritaire. Exemple :

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

Pour modifier le nom complet d’un ensemble de règles qui est ouvert dans l’éditeur, ouvrez la fenêtre **Propriétés** en sélectionnant **affichage** > **fenêtre Propriétés** dans la barre de menus. Entrez le nom d’affichage dans la zone **nom** . Vous pouvez également entrer une description pour l’ensemble de règles.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous disposez d’un ensemble de règles, l’étape suivante consiste à personnaliser les règles en ajoutant ou en supprimant des règles ou en modifiant la gravité des violations de règle.

> [!div class="nextstepaction"]
> [Modifier les règles dans l’éditeur d’ensembles de règles](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour configurer l’analyse du code pour un projet de code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Informations de référence sur l’ensemble de règles d’analyse du code](../code-quality/rule-set-reference.md)

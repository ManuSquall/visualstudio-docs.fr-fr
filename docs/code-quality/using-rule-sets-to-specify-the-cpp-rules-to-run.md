---
title: Utilisation des ensembles de règles pour spécifier les règles C++ à exécuter
ms.date: 04/28/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: d4d7dfc1f010b860653edbe14fa7af9050bddba4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820371"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Utilisez des ensembles de règles pour spécifier les règles C++ à exécuter

Dans Visual Studio, vous pouvez créer et modifier un personnalisé *ensemble de règles* pour répondre aux besoins spécifiques de projet associés à l’analyse du code. Les ensembles de règles par défaut sont stockés dans `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 version 15.7 et ultérieure** vous pouvez créer des ensembles de règles personnalisés à l’aide de n’importe quel texte éditeur et appliquez-les dans les versions de ligne de commande, quel que soit ce que vous utilisez de système de génération. Pour plus d’informations, consultez [/ analyze : ruleset](/cpp/build/reference/analyze-code-analysis).

Pour créer une règle de C++ personnalisée définie dans Visual Studio, un projet C/C++ doit être ouvert dans l’IDE Visual Studio. Vous puis ouvrez un ensemble de règles standard dans l’éditeur d’ensemble de règles et puis ajoutez ou supprimez des règles spécifiques et éventuellement modifiez l’action qui se produit lorsque l’analyse du code détermine qu’une règle a été violée.

Pour créer une nouvelle règle personnalisée définie, vous l’enregistrez à l’aide d’un nouveau nom de fichier. L’ensemble de règles personnalisé est automatiquement affecté au projet.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Pour créer une règle personnalisée à partir d’un seul ensemble de règles existant

1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du projet, puis choisissez **propriétés**.

2. Sur le **propriétés** , choisir **analyse du Code**.

3. Dans le **l’ensemble de règles** liste déroulante, effectuez l’une des opérations suivantes :

   - Choisissez l’ensemble de règles que vous souhaitez personnaliser.

     \- ou -

   - Choisissez  **\<Parcourir... >** pour spécifier une règle existante définie qui n’est pas dans la liste.

4. Choisissez **Open** pour afficher les règles dans l’éditeur d’ensemble de règles.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Pour modifier une règle définie dans l’éditeur d’ensemble de règles

- Pour modifier le nom complet de l’ensemble de règles, dans le **vue** menu, choisissez **fenêtre Propriétés**. Entrez le nom d’affichage dans le **nom** boîte. Notez que le nom de l’affichage peut différer du nom du fichier.

- Pour ajouter toutes les règles du groupe à un ensemble de règles personnalisé, sélectionnez la case à cocher du groupe. Pour supprimer toutes les règles du groupe, désactivez la case à cocher.

- Pour ajouter une règle spécifique à l’ensemble de règles personnalisé, sélectionnez la case à cocher de la règle. Pour supprimer la règle à partir de l’ensemble de règles, désactivez la case à cocher.

- Pour modifier l’action effectuée lorsqu’une règle est violée dans une analyse du code, choisissez la **Action** champ pour la règle et choisissez l’une des valeurs suivantes :

     **Avertir** -génère un avertissement.

     **Erreur** -génère une erreur.

     **Aucun** -désactive la règle. Cette action est le même que la suppression de la règle de l’ensemble de règles.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Pour regrouper, filtrer ou modifier les champs dans l’éditeur d’ensemble de règles à l’aide de la barre d’outils Éditeur de règle ensemble

- Pour développer les règles dans tous les groupes, choisissez **développer tout**.

- Pour réduire les règles dans tous les groupes, choisissez **réduire tout**.

- Pour modifier le champ dont les règles sont regroupés, choisissez le champ à partir de la **Group By** liste. Pour afficher les règles non groupées, choisissez  **\<None >** .

- Pour ajouter ou supprimer des champs dans les colonnes de la règle, choisissez **Options de colonne**.

- Pour masquer les règles qui ne s’appliquent pas à la solution actuelle, choisissez **masquer des règles qui ne s’appliquent pas à la solution actuelle**.

- Pour basculer entre l’affichage et masquage des règles qui sont affectés à l’action d’erreur, choisissez **afficher les règles qui peuvent générer des erreurs d’analyse du Code**.

- Pour basculer entre l’affichage et masquage des règles qui sont affectés à l’action de l’avertissement, choisissez **afficher les règles qui peuvent générer des avertissements d’analyse du Code**.

- Pour basculer entre l’affichage et masquage des règles qui sont affectées la **aucun** action, choisissez **afficher les règles qui ne sont pas activés**.

- Pour ajouter ou supprimer des ensembles de règles de valeur par défaut à l’ensemble de règles actuel de Microsoft, choisissez **ajouter ou supprimer des ensembles de règles enfants**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Pour créer un ensemble de règles dans un éditeur de texte

Vous pouvez créer un ensemble de règles personnalisé dans un texte de l’éditeur, stockez-le dans n’importe quel emplacement avec un `.ruleset` extension et s’appliquent à l’aide du [/ analyze : ruleset](/cpp/build/reference/analyze-code-analysis) option du compilateur.

L’exemple suivant montre qu'une règle de base défini le fichier que vous pouvez utiliser comme point de départ :

::: moniker range="vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

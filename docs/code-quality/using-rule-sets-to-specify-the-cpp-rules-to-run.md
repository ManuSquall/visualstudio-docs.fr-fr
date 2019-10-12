---
title: Utilisation des ensembles de règles pour spécifier les règles C++ à exécuter
ms.date: 04/28/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.native
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 64421350f74a2fadcb8a4d4845d8aa00a5f5813b
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163101"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Utiliser des ensembles de règles pour C++ spécifier les règles à exécuter

Dans Visual Studio, vous pouvez créer et modifier un *ensemble de règles* personnalisé pour répondre à des besoins de projet spécifiques associés à l’analyse du code. Les ensembles de règles par défaut sont stockés dans `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 15.7 et versions ultérieures :** Vous pouvez créer des ensembles de règles personnalisés à l’aide de n’importe quel éditeur de texte et les appliquer dans les builds de ligne de commande, quel que soit le système de génération que vous utilisez. Pour plus d’informations, consultez [/analyze : RuleSet](/cpp/build/reference/analyze-code-analysis).

Pour créer un ensemble C++ de règles personnalisé dans Visual Studio, un projetC++ C/doit être ouvert dans l’IDE de Visual Studio. Vous ouvrez ensuite un ensemble de règles standard dans l’éditeur d’ensembles de règles, puis vous ajoutez ou supprimez des règles spécifiques et modifiez éventuellement l’action qui se produit lorsque l’analyse du code détermine qu’une règle a été violée.

Pour créer un ensemble de règles personnalisé, enregistrez-le à l’aide d’un nouveau nom de fichier. L’ensemble de règles personnalisé est automatiquement affecté au projet.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Pour créer une règle personnalisée à partir d’un seul ensemble de règles existant

1. Dans la Explorateur de solutions, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.

2. Sous l’onglet **Propriétés** , choisissez **analyse du code**.

3. Dans la liste déroulante **ensemble de règles** , effectuez l’une des opérations suivantes :

   - Choisissez l’ensemble de règles que vous souhaitez personnaliser.

     \- ou -

   - Choisissez **\<Browse... >** pour spécifier un ensemble de règles existant qui ne figure pas dans la liste.

4. Choisissez **ouvrir** pour afficher les règles dans l’éditeur d’ensembles de règles.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Pour modifier un ensemble de règles dans l’éditeur d’ensembles de règles

- Pour modifier le nom complet de l’ensemble de règles, dans le menu **affichage** , choisissez **fenêtre Propriétés**. Entrez le nom d’affichage dans la zone **nom** . Notez que le nom d’affichage peut être différent du nom de fichier.

- Pour ajouter toutes les règles du groupe à un ensemble de règles personnalisé, activez la case à cocher du groupe. Pour supprimer toutes les règles du groupe, désactivez la case à cocher.

- Pour ajouter une règle spécifique à l’ensemble de règles personnalisé, activez la case à cocher de la règle. Pour supprimer la règle de l’ensemble de règles, désactivez la case à cocher.

- Pour modifier l’action entreprise lorsqu’une règle est violée dans une analyse du code, choisissez le champ **action** pour la règle, puis choisissez l’une des valeurs suivantes :

     **Avertissement** : génère un avertissement.

     **Erreur** : génère une erreur.
     
     **Info** -génère un message.

     **None** : désactive la règle. Cette action revient à supprimer la règle de l’ensemble de règles.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Pour regrouper, filtrer ou modifier les champs de l’éditeur d’ensembles de règles à l’aide de la barre d’outils Éditeur d’ensemble de règles

- Pour développer les règles de tous les groupes, choisissez **développer tout**.

- Pour réduire les règles de tous les groupes, choisissez **réduire tout**.

- Pour modifier le champ par lequel les règles sont regroupées, choisissez le champ dans la liste **regrouper par** . Pour afficher les règles non groupées, choisissez **\<None >** .

- Pour ajouter ou supprimer des champs dans les colonnes de règles, choisissez **options de colonne**.

- Pour masquer les règles qui ne s’appliquent pas à la solution actuelle, choisissez **Masquer les règles qui ne s’appliquent pas à la solution actuelle**.

- Pour basculer entre l’affichage et le masquage des règles affectées par l’action d’erreur, choisissez **afficher les règles qui peuvent générer des erreurs d’analyse du code**.

- Pour basculer entre l’affichage et le masquage des règles affectées par l’action d’avertissement, choisissez **afficher les règles qui peuvent générer des avertissements d’analyse du code**.

- Pour basculer entre l’affichage et le masquage des règles affectées par l’action **aucun** , choisissez **afficher les règles qui ne sont pas activées**.

- Pour ajouter ou supprimer des ensembles de règles par défaut Microsoft pour l’ensemble de règles actuel, choisissez **Ajouter ou supprimer des ensembles de règles enfants**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Pour créer un ensemble de règles dans un éditeur de texte

Vous pouvez créer un ensemble de règles personnalisé dans un éditeur de texte, le stocker dans n’importe quel emplacement avec une extension `.ruleset`, et l’appliquer à l’aide de l’option de compilateur [/analyze : RuleSet](/cpp/build/reference/analyze-code-analysis) .

L’exemple suivant montre un fichier d’ensemble de règles de base que vous pouvez utiliser comme point de départ :

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
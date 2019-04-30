---
title: Utiliser l’éditeur de jeu de règles Code Analysis
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 719d8f1e11365de0b864f41f54546fb4bfc64cd2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820312"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Utiliser l’éditeur de jeu de règles code analysis

La règle d’analyse du code définie éditeur vous permet de que spécifier les règles qui sont inclus dans une règle personnalisée définie et définir le niveau de gravité des violations de règle.

Le tableau suivant présente les options de niveau de gravité :

|Action (gravité)|Description|
|-|-|
|Warning|Génère un avertissement dans le **liste d’erreurs** et également au moment de la génération.|
|Error|Génère une erreur dans le **liste d’erreurs** et également au moment de la génération.|
|Info|Génère un message dans le **liste d’erreurs**.|
|Hidden|La violation n’est pas visible à l’utilisateur. L’IDE est averti de la violation, toutefois.|
|Aucun.|La règle est supprimée. Le comportement est le même que si la règle a été supprimée de l’ensemble de règles.|

L’éditeur affiche les règles dans une structure arborescente qui groupe les règles par une règle de définie le champ que vous spécifiez. Pour ajouter ou supprimer des règles à partir d’un ensemble de règles, effectuer une ou plusieurs des étapes suivantes :

- Activez ou désactivez la case à cocher du nœud de groupe pour ajouter ou supprimer toutes les règles dans le groupe. Lorsque vous sélectionnez un groupe, toutes les règles sont définies le **avertissement** action.

   > [!TIP]
   > Vous pouvez modifier la façon dont les règles sont regroupés dans le **Group by** liste déroulante.

- Cliquez sur le **Action** champ d’un groupe, puis spécifiez l’action à appliquer à toutes les règles dans le groupe.

- Activez ou désactivez la case à cocher pour une règle individuelle. Lorsque vous sélectionnez la case à cocher pour une règle, la règle est définie à l’action de l’avertissement.

## <a name="toolbar"></a>ToolBar

Vous pouvez utiliser la barre d’outils de l’éditeur d’ensemble de règles pour regrouper, filtrer et rechercher les données qui s’affiche dans la grille de jeu de règles.

Le tableau suivant décrit les contrôles sur la barre d’outils de l’éditeur d’ensemble de règles.

|Contrôle de barre d’outils|Description|
|---------------------|-----------------|
|**Développer tout**|Affiche les règles dans tous les groupes.|
|**Réduire tout**|Masque les règles dans tous les groupes.|
|**Group By**|Spécifie le champ selon lequel les règles sont groupées. Cliquez sur  **\<None >** pour afficher les règles sans les groupes.|
|**Options de colonne**|Spécifie les champs de règle à afficher.|
|**Masquer les règles qui ne s’appliquent pas à la solution actuelle**|Affiche ou masque les règles qui ne sont pas du même Type de cible comme la solution.|
|**Afficher les règles qui peuvent générer des erreurs d’analyse du Code**|Affiche ou masque les règles qui sont affectés à l’action d’erreur.|
|**Afficher les règles qui peuvent générer des avertissements d’analyse du Code**|Affiche ou masque les règles qui sont affectés à l’action de l’avertissement.|
|**Afficher les règles qui ne sont pas activés**|Affiche ou masque les règles qui sont affectés à aucune action.|
|**Ajouter ou supprimer des ensembles de règles enfants**|Ajoute ou supprime les règles dans les ensembles de règles sélectionné.|
|**Règles de recherche**|Recherche toutes les valeurs de champ pour la chaîne que vous spécifiez.|

## <a name="rule-set-fields"></a>Champs d’ensemble de règles

Jeu de champs de règle d’affichent des informations sur un ensemble de règles et peuvent être utilisées pour trier et regrouper la liste des règles. Pour afficher ou masquer des champs, sélectionnez **Options de colonne** sur la règle de définir la barre d’outils de l’éditeur, puis activez ou désactivez les cases à cocher des champs à afficher ou masquer.

Le tableau suivant décrit les champs d’un ensemble de règles :

|Champ|Description|
|-----------|-----------------|
|**ID**|L’identificateur de la règle.|
|**Catégorie**|En plus de leur appartenance aux ensembles de règles, les règles d’analyse du code sont également groupées par catégorie. Pour plus d’informations, consultez [avertissements d’analyse du Code](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|Le titre de la règle.|
|**Espace de noms**|L’espace de noms de la règle.|
|**Type de cible**|Indique si la règle concerne natif, managé ou code base de données.|
|**Action**|L’action effectuée lorsque la règle est violée dans une analyse du code s’exécuter. Vous pouvez modifier le **Action** champ.|
|**Ensembles de règles de source**|L’ensemble de règles qui contient la règle.|

## <a name="sort-and-filter-rule-sets"></a>Trier et filtrer les ensembles de règles

À partir des en-têtes de colonnes de la grille de jeu de règles, vous pouvez trier et filtrer les règles par les valeurs du champ.

- Pour trier les listes de jeu de règle, cliquez sur l’en-tête de colonne du champ en fonction duquel vous voulez trier. Si les ensembles de règles sont regroupées, chaque groupe est trié individuellement.

- Pour filtrer les ensembles de règles par la valeur d’un champ, cliquez sur le bouton de filtre sur l’en-tête de colonne du champ par lequel vous souhaitez filtrer. Sélectionnez les cases à cocher des valeurs que vous souhaitez afficher et désactivez les cases à cocher des valeurs que vous souhaitez masquer.

## <a name="see-also"></a>Voir aussi

- [Créer un ensemble de règles personnalisé](../code-quality/how-to-create-a-custom-rule-set.md)
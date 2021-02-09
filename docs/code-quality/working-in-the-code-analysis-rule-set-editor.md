---
title: Utiliser l'Éditeur d'ensembles de règles d'analyse du code
ms.date: 04/04/2018
description: Découvrez comment modifier et afficher les ensembles de règles dans Visual Studio. Consultez Comment définir la gravité d’une règle, spécifier des règles dans un ensemble personnalisé et ajuster les données dans la grille de l’ensemble de règles.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ba8ecdd3a1aae382d1b74d75e26e614ba07e6a66
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867605"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Utiliser l’éditeur d’ensembles de règles d’analyse du code

L’éditeur d’ensembles de règles d’analyse du code vous permet de spécifier les règles incluses dans un ensemble de règles personnalisé et de définir la gravité des violations de règle.

Le tableau suivant présente les options de gravité :

|Action (gravité)|Description|
|-|-|
|Avertissement|Génère un avertissement dans le **liste d’erreurs** et également au moment de la génération.|
|Erreur|Génère une erreur dans le **liste d’erreurs** et également au moment de la génération.|
|Informations|Génère un message dans le **liste d’erreurs**.|
|Hidden|La violation n’est pas visible pour l’utilisateur. Toutefois, l’IDE est averti de la violation.|
|None|La règle est supprimée. Le comportement est le même que si la règle a été supprimée de l’ensemble de règles.|

L’éditeur affiche les règles dans une arborescence qui regroupe les règles par un champ d’ensemble de règles que vous spécifiez. Pour ajouter ou supprimer des règles dans un ensemble de règles, effectuez une ou plusieurs des étapes suivantes :

- Activez ou désactivez la case à cocher du nœud Groupe pour ajouter ou supprimer toutes les règles du groupe. Lorsque vous sélectionnez un groupe, toutes les règles sont définies sur l’action d' **Avertissement** .

   > [!TIP]
   > Vous pouvez modifier la façon dont les règles sont regroupées dans la liste déroulante **regrouper par** .

- Cliquez sur le champ **action** d’un groupe, spécifiez l’action à appliquer à toutes les règles du groupe.

- Activez ou désactivez la case à cocher d’une règle individuelle. Lorsque vous activez la case à cocher d’une règle, la règle est définie sur l’action d' **Avertissement** .

## <a name="toolbar"></a>Barre d’outils

Vous pouvez utiliser la barre d’outils de l’éditeur d’ensembles de règles pour regrouper, filtrer et rechercher les données qui s’affichent dans la grille d’ensemble de règles.

Le tableau suivant décrit les contrôles de la barre d’outils de l’éditeur d’ensembles de règles.

|Toolbar, contrôle|Description|
|---------------------|-----------------|
|**Développer tout**|Affiche les règles dans tous les groupes.|
|**Réduire tout**|Masque les règles dans tous les groupes.|
|**Regrouper par**|Spécifie le champ selon lequel les règles sont regroupées. Cliquez **\<None>** pour afficher les règles sans groupes.|
|**options de colonne**|Spécifie les champs de règle à afficher.|
|**Masquer les règles qui ne s’appliquent pas à la solution actuelle**|Affiche ou masque les règles qui ne sont pas du même type de cible que la solution.|
|**Afficher les règles qui peuvent générer des erreurs d’analyse du code**|Affiche ou masque les règles auxquelles l’action d’erreur est assignée.|
|**Afficher les règles qui peuvent générer des avertissements d’analyse du code**|Affiche ou masque les règles auxquelles l’action d’avertissement est assignée.|
|**Afficher les règles qui ne sont pas activées**|Affiche ou masque les règles auxquelles l’action None est affectée.|
|**Ajouter ou supprimer des ensembles de règles enfants**|Ajoute ou supprime les règles dans les ensembles de règles sélectionnés.|
|**Règles de recherche**|Recherche toutes les valeurs de champ pour la chaîne que vous spécifiez.|

## <a name="rule-set-fields"></a>Champs d’ensemble de règles

Les champs d’ensemble de règles affichent des informations sur un ensemble de règles et peuvent être utilisés pour trier et regrouper la liste des règles. Pour afficher ou masquer des champs, sélectionnez **options de colonne** dans la barre d’outils de l’éditeur d’ensembles de règles, puis activez ou désactivez les cases à cocher des champs à afficher ou à masquer.

Le tableau suivant décrit les champs d’un ensemble de règles :

|Champ|Description|
|-----------|-----------------|
|**Identifiant**|Identificateur de la règle.|
|**Catégorie**|Outre leur appartenance aux ensembles de règles, les règles d’analyse du code sont également regroupées par catégorie. Pour plus d’informations, consultez [avertissements d’analyse du code](/dotnet/fundamentals/code-analysis/quality-rules/index).|
|**Nom**|Titre de la règle.|
|**Espace de noms**|Espace de noms de la règle.|
|**Type de cible**|Indique si la règle est pour le code natif, managé ou de base de données.|
|**Action**|Action entreprise lorsque la règle n’est pas respectée lors d’une exécution de l’analyse du code. Vous pouvez modifier le champ **action** .|
|**Ensembles de règles sources**|Ensemble de règles qui contient la règle.|

## <a name="sort-and-filter-rule-sets"></a>Trier et filtrer les ensembles de règles

À partir des en-têtes de colonne de la grille de l’ensemble de règles, vous pouvez trier et filtrer les règles selon les valeurs du champ.

- Pour trier les listes d’ensembles de règles, sélectionnez l’en-tête de colonne du champ sur lequel vous souhaitez effectuer le tri. Si les ensembles de règles sont regroupés, chaque groupe est trié individuellement.

- Pour filtrer les ensembles de règles en fonction de la valeur d’un champ, sélectionnez le bouton de filtre sur l’en-tête de colonne du champ en fonction duquel vous voulez effectuer le filtrage. Activez les cases à cocher des valeurs que vous souhaitez afficher et désactivez les cases à cocher des valeurs que vous souhaitez masquer.

## <a name="see-also"></a>Voir aussi

- [Créer un ensemble de règles personnalisé](../code-quality/how-to-create-a-custom-rule-set.md)

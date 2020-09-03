---
title: Utilisation de l’éditeur d’ensembles de règles d’analyse du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f25cc5a5f56c20f6a1696baa5aa3e9ee5ebdf2fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621509"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Utilisation de l'Éditeur d'ensembles de règles d'analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’éditeur d’ensembles de règles d’analyse du code vous permet de spécifier les règles incluses dans un ensemble de règles personnalisé et de spécifier l’action. Vous pouvez également spécifier l’action à entreprendre lorsque l’analyse du code rencontre une violation de la règle.

|Action|Description|
|------------|-----------------|
|**Avertissement**|Génère un avertissement dans la fenêtre de **liste d’erreurs** .|
|**Erreur**|Génère une erreur dans la fenêtre de **liste d’erreurs** .|
|**Aucun**|Désactive la règle.|

 L’éditeur affiche les règles dans une arborescence qui regroupe les règles par un champ d’ensemble de règles que vous spécifiez. Pour ajouter ou supprimer des règles dans un ensemble de règles, effectuez une ou plusieurs des étapes suivantes :

- Activez ou désactivez la case à cocher du nœud Groupe pour ajouter ou supprimer toutes les règles du groupe. Lorsque vous sélectionnez un groupe, toutes les règles sont définies sur l’action d' **Avertissement** .

- Cliquez sur le champ **action** d’un groupe, puis spécifiez l’action à appliquer à toutes les règles du groupe.

- Activez ou désactivez la case à cocher d’une règle individuelle. Lorsque vous activez la case à cocher d’une règle, la règle est définie sur l’action d’avertissement.

## <a name="rule-set-editor-toolbar"></a>Barre d’outils de l’éditeur d’ensembles de règles
 Vous pouvez utiliser la barre d’outils de l’éditeur d’ensembles de règles pour regrouper, filtrer et rechercher les données qui s’affichent dans la grille d’ensemble de règles.

 Le tableau suivant décrit les contrôles de la barre d’outils de l’éditeur d’ensembles de règles.

|Toolbar, contrôle|Description|
|---------------------|-----------------|
|**Développer tout**|Affiche les règles dans tous les groupes.|
|**Réduire tout**|Masque les règles dans tous les groupes.|
|**Regrouper par**|Spécifie le champ selon lequel les règles sont regroupées. Cliquez **\<None>** pour afficher les règles sans groupes.|
|**Options de colonne**|Spécifie les champs de règle à afficher.|
|**Masquer les règles qui ne s’appliquent pas à la solution actuelle**|Affiche ou masque les règles qui ne sont pas du même type de cible que la solution.|
|**Afficher les règles qui peuvent générer des erreurs d’analyse du code**|Affiche ou masque les règles auxquelles l’action d’erreur est assignée.|
|**Afficher les règles qui peuvent générer des avertissements d’analyse du code**|Affiche ou masque les règles auxquelles l’action d’avertissement est assignée.|
|**Afficher les règles qui ne sont pas activées**|Affiche ou masque les règles auxquelles l’action None est affectée.|
|**Ajouter ou supprimer des ensembles de règles enfants**|Ajoute ou supprime les règles dans les ensembles de règles sélectionnés.|
|**Règles de recherche**|Recherche toutes les valeurs de champ pour la chaîne que vous spécifiez.|

## <a name="rule-set-fields"></a>Champs d’ensemble de règles
 Les champs d’ensemble de règles affichent des informations sur un ensemble de règles et peuvent être utilisés pour trier et regrouper la liste des règles. Pour afficher ou masquer des champs, cliquez sur **options de colonne** dans la barre d’outils de l’éditeur d’ensembles de règles, puis activez ou désactivez les cases à cocher des champs à afficher ou à masquer.

 Le tableau suivant décrit les champs d’un ensemble de règles.

|Champ|Description|
|-----------|-----------------|
|**Identifiant**|Identificateur de la règle.|
|**Catégorie**|Outre leur appartenance aux ensembles de règles, les règles d’analyse du code sont également regroupées par catégorie. Pour plus d’informations, consultez [analyse du code pour les avertissements de code managé](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Nom**|Titre de la règle.|
|**Espace de noms**|Espace de noms de la règle.|
|**Type de cible**|Indique si la règle est pour le code natif, managé ou de base de données.|
|**Action**|Action entreprise lorsque la règle n’est pas respectée lors d’une exécution de l’analyse du code.<br /><br /> **Avertissement** : génère un avertissement.<br /><br /> **Erreur** : génère une erreur.<br /><br /> **None** : désactive la règle.<br /><br /> Vous pouvez modifier le champ action. La définition de la valeur sur aucun est identique à la désactivation de la case à cocher de la règle.|
|**Ensembles de règles sources**|Ensemble de règles qui contient la règle.|

## <a name="sorting-and-filtering-rule-sets"></a>Tri et filtrage des ensembles de règles
 À partir des en-têtes de colonne de la grille de l’ensemble de règles, vous pouvez trier et filtrer les règles selon les valeurs du champ.

- Pour trier les listes d’ensembles de règles, cliquez sur l’en-tête de colonne du champ sur lequel vous souhaitez effectuer le tri. Si les ensembles de règles sont regroupés, chaque groupe est trié individuellement.

- Pour filtrer les ensembles de règles en fonction de la valeur d’un champ, cliquez sur le bouton de filtre sur l’en-tête de colonne du champ en fonction duquel vous voulez effectuer le filtrage. Activez les cases à cocher des valeurs que vous souhaitez afficher et désactivez les cases à cocher des valeurs que vous souhaitez masquer.

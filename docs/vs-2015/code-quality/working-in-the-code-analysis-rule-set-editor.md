---
title: Éditeur de jeu de travail dans la règle d’analyse de Code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 57d3c21371cc824573e29657d0b41253e556f4c3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072251"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Utilisation de l'Éditeur d'ensembles de règles d'analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’éditeur d’ensembles de règles analyse du Code vous permet de spécifier les règles qui sont inclus dans un ensemble de règles personnalisé et pour spécifier l’action. Vous pouvez également spécifier l’action à entreprendre lorsque l’analyse du code rencontre une violation de la règle.  
  
|Action|Description|  
|------------|-----------------|  
|**Avertissement**|Génère un avertissement dans le **liste d’erreurs** fenêtre.|  
|**Error**|Génère une erreur dans le **liste d’erreurs** fenêtre.|  
|**Aucun**|Désactive la règle.|  
  
 L’éditeur affiche les règles dans une structure arborescente qui groupe les règles par une règle de définie le champ que vous spécifiez. Pour ajouter ou supprimer des règles à partir d’un ensemble de règles, effectuer une ou plusieurs des étapes suivantes :  
  
- Activez ou désactivez la case à cocher du nœud de groupe pour ajouter ou supprimer toutes les règles dans le groupe. Lorsque vous sélectionnez un groupe, toutes les règles sont définies le **avertissement** action.  
  
- Cliquez sur le **Action** champ d’un groupe, puis spécifiez l’action à appliquer à toutes les règles dans le groupe.  
  
- Activez ou désactivez la case à cocher pour une règle individuelle. Lorsque vous sélectionnez la case à cocher pour une règle, la règle est définie à l’action de l’avertissement.  
  
## <a name="rule-set-editor-toolbar"></a>Barre d’outils Éditeur d’ensemble de règles  
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
  
## <a name="rule-set-fields"></a>Champs de règle d’ensemble  
 Champs affichent des informations relatives à une règle définie et peuvent être utilisées pour trier et regrouper la liste des règles d’ensemble de règles. Pour afficher ou masquer des champs, cliquez sur **Options de colonne** sur la règle de définir la barre d’outils de l’éditeur, puis activez ou désactivez les cases à cocher des champs à afficher ou masquer.  
  
 Le tableau suivant décrit les champs d’un ensemble de règles.  
  
|Champ|Description|  
|-----------|-----------------|  
|**ID**|L’identificateur de la règle.|  
|**Catégorie**|En plus de leur appartenance aux ensembles de règles, les règles d’analyse du code sont également groupées par catégorie. Pour plus d’informations, consultez [analyse du Code pour les avertissements de Code géré](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Name**|Le titre de la règle.|  
|**Espace de noms**|L’espace de noms de la règle.|  
|**Type de cible**|Indique si la règle concerne natif, managé ou code base de données.|  
|**Action**|L’action effectuée lorsque la règle est violée dans une analyse du code s’exécuter.<br /><br /> **Avertissement** -génère un avertissement.<br /><br /> **Erreur** -génère une erreur.<br /><br /> **Aucun** -désactive la règle.<br /><br /> Vous pouvez modifier le champ d’Action. Définition de la valeur None est au même que décocher la case à cocher pour la règle.|  
|**Ensembles de règles de source**|L’ensemble de règles qui contient la règle.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Tri et filtrage des ensembles de règles  
 À partir des en-têtes de colonnes de la grille de jeu de règles, vous pouvez trier et filtrer les règles par les valeurs du champ.  
  
- Pour trier les listes de jeu de règle, cliquez sur l’en-tête de colonne du champ en fonction duquel vous voulez trier. Si les ensembles de règles sont regroupées, chaque groupe est trié individuellement.  
  
- Pour filtrer les ensembles de règles par la valeur d’un champ, cliquez sur le bouton de filtre sur l’en-tête de colonne du champ par lequel vous souhaitez filtrer. Sélectionnez les cases à cocher des valeurs que vous souhaitez afficher et désactivez les cases à cocher des valeurs que vous souhaitez masquer.

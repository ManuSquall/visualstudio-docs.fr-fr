---
title: "Utilisation de l&#39;&#201;diteur d&#39;ensembles de r&#232;gles d&#39;analyse du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.ruleseteditor"
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Utilisation de l&#39;&#201;diteur d&#39;ensembles de r&#232;gles d&#39;analyse du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'éditeur d'ensembles de règles d'analyse du code vous permet de spécifier les règles incluses dans un ensemble de règles personnalisé et de spécifier l'action à mener.  Vous pouvez également spécifier cette action lorsque l'analyse du code est confrontée à une violation de la règle.  
  
|Action|Description|  
|------------|-----------------|  
|**Warning**|Génère un avertissement dans la fenêtre **Liste d'erreurs**.|  
|**Error**|Génère une erreur dans la fenêtre **Liste d'erreurs**.|  
|**None**|Désactive la règle.|  
  
 L'éditeur affiche les règles dans une arborescence qui groupe les règles par un champ d'ensemble de règles que vous spécifiez.  Pour ajouter ou supprimer des règles d'un ensemble de règles, exécutez une ou plusieurs des étapes suivantes :  
  
-   Sélectionnez ou désactivez la case à cocher du nœud de groupe pour ajouter ou supprimer toutes les règles dans le groupe.  Lorsque vous sélectionnez un groupe, toutes les règles ont la valeur de l'action **Warning**.  
  
-   Cliquez sur le champ **Action** d'un groupe, puis spécifiez l'action à appliquer à toutes les règles dans le groupe.  
  
-   Sélectionnez ou désactivez la case à cocher pour une règle individuelle.  Lorsque vous sélectionnez la case à cocher pour une règle, la règle a la valeur de l'action Warning.  
  
## Barre d'outils de l'éditeur d'ensembles de règles  
 Vous pouvez utiliser la barre d'outils de l'éditeur d'ensembles de règles pour grouper, filtrer et rechercher les données qui s'affichent dans la grille d'ensembles de règles.  
  
 Le tableau suivant décrit les contrôles sur la barre d'outils de l'éditeur d'ensembles de règles.  
  
|Contrôle de barre d'outils|Description|  
|--------------------------------|-----------------|  
|**Développer tout**|Affiche les règles dans tous les groupes.|  
|**Réduire tout**|Masque les règles dans tous les groupes.|  
|**Group By**|Spécifie le champ par lequel les règles sont groupées.  Cliquez sur **\<None\>** pour afficher les règles sans les groupes.|  
|**Options de colonne**|Spécifie les champs de règle à afficher.|  
|**Masquer les règles qui ne s'appliquent pas à la solution actuelle**|Affiche ou masque les règles qui ne sont pas du même type de cible que la solution.|  
|**Afficher les règles qui peuvent générer des erreurs d'analyse du code**|Affiche ou masque les règles assignées à l'action Error.|  
|**Afficher les règles qui peuvent générer des avertissements d'analyse du code**|Affiche ou masque les règles auxquelles est assignée l'action Warning.|  
|**Afficher les règles qui ne sont pas activées**|Affiche ou masque les règles auxquelles est assignée l'action None.|  
|**Ajouter ou supprimer les ensembles de règles enfants**|Ajoute ou supprime les règles dans les ensembles de règles sélectionnés.|  
|**Règles de recherche**|Recherche la chaîne que vous spécifiez dans toutes les valeurs de champ.|  
  
## Champs d'ensembles de recherche  
 Les champs d'ensembles de règles affichent les informations concernant un ensemble de règles et peuvent être utilisés pour trier et grouper la liste de règles.  Pour afficher ou masquer des champs, cliquez sur **Options de colonne** dans la barre d'outils de l'éditeur d'ensembles de règles, puis vérifiez ou désactivez les cases à cocher des champs pour les afficher ou les masquer.  
  
 Le tableau suivant décrit les champs de l'ensemble de règles.  
  
|Champ|Description|  
|-----------|-----------------|  
|**ID**|Identificateur de la règle.|  
|**Category**|Outre leur appartenance aux ensembles de règles, les règles d'analyse du code sont également groupées par catégorie.  Pour plus d'informations, consultez [Analyse du code pour les avertissements liés au code managé](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Name**|Titre de la règle .|  
|**Namespace**|Espace de noms de la règle.|  
|**Target Type**|Indique si la règle est destinée au code natif, au code managé ou au code de base de données.|  
|**Action**|Action prise lorsque la règle est enfreinte lors de l'exécution d'une analyse du code.<br /><br /> **Warning** \- génère un avertissement.<br /><br /> **Error** \- génère une erreur.<br /><br /> **None** \- désactive la règle.<br /><br /> Vous pouvez modifier le champ Action.  L'affectation de la valeur \<None\> revient à désactiver la case à cocher pour la règle.|  
|**Source Rule Sets**|Ensemble de règles qui contient la règle.|  
  
## Tri et filtrage des ensembles de règles  
 À partir des en\-têtes de colonnes de la grille d'ensembles de règles, vous pouvez trier et filtrer les règles par les valeurs de champ.  
  
-   Pour trier les listes d'ensembles de règles, cliquez sur l'en\-tête de colonne du champ par lequel vous souhaitez trier.  Si les ensembles de règles sont groupés, chaque groupe est trié individuellement.  
  
-   Pour filtrer les ensembles de règles par la valeur d'un champ, cliquez sur le bouton de filtre sur l'en\-tête de colonne du champ par lequel vous souhaitez filtrer.  Activez les cases à cocher des valeurs que vous voulez afficher et désactivez les cases à cocher des valeurs que vous voulez masquer.
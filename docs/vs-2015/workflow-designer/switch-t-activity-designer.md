---
title: Commutateur&lt;T&gt; Concepteur d’activités | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e2baacdfb35e2360a0e9dcc56891cadbe7d3ff3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951994"
---
# <a name="switchlttgt-activity-designer"></a>Commutateur&lt;T&gt; Concepteur d’activités
L'activité <xref:System.Activities.Statements.Switch%601> évalue une expression spécifiée et exécute l'activité à partir d'une collection d'activités dont la clé associée correspond à la valeur obtenue de l'évaluation.  
  
 Le **commutateur\<T >** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Switch%601> activité dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
## <a name="the-switchtactivity"></a>Le commutateur\<T > activité  
 Une activité <xref:System.Activities.Statements.Switch%601> contient une propriété <xref:System.Activities.Statements.Switch%601.Expression%2A> et un dictionnaire de propriétés <xref:System.Activities.Statements.Switch%601.Cases%2A>. Chaque cas dans le dictionnaire se compose d’une paire qui contient un *clé* et une activité qui lui sert *valeur*. L'activité <xref:System.Activities.Statements.Switch%601> évalue la propriété <xref:System.Activities.Statements.Switch%601.Expression%2A> et la compare à chacune des clés. Si une correspondance est trouvée, l'activité correspondante est exécutée. Une seule correspondance est possible, car les clés de dictionnaire doivent être uniques par rapport au type d'égalité défini par le comparateur d'égalité du dictionnaire. Si aucune correspondance n'est trouvée, l'activité <xref:System.Activities.Statements.Switch%601.Default%2A> est exécutée.  
  
## <a name="how-to-use-the-switcht-activity-designer"></a>Comment utiliser le commutateur\<T > Concepteur d’activités  
 Le **commutateur\<T >** Concepteur d’activités peut être trouvé dans le **flux de contrôle** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **Boîte à outils** onglet sur le [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.) Une fois déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)], il affiche le **sélectionner les Types** boîte de dialogue pour permettre à l’utilisateur de spécifier le type générique *T* utilisé dans <xref:System.Activities.Statements.Switch%601> activité. La valeur par défaut est **Int32**. Une fois que le type générique *T* a été sélectionné, un **commutateur\<T >** concepteur est ajouté dans le Concepteur de flux de travail.  
  
 Voici les propriétés de **commutateur\<T >** concepteur. Toutes ces propriétés peuvent être modifiées dans la grille des propriétés. Certaines peuvent également être modifiées dans l'aire du concepteur.  
  
 Le tableau suivant répertorie les propriétés de l'activité <xref:System.Activities.Statements.Switch%601> qui sont les plus utiles et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Switch%601>. La valeur par défaut est Switch\<Int32 >. La valeur peut être modifiée dans le **propriétés** fenêtre ou directement sur l’en-tête du concepteur.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Spécifie l'expression à comparer aux clés dans la collection de cas pour déterminer le cas à exécuter.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Spécifie l'activité exécutée si aucune correspondance n'est trouvée. Cliquez sur le **ajouter une activité** bouton sur le concepteur pour ouvrir le **par défaut** zone où l’activité peut être supprimée.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Spécifie les cas à évaluer. Pour ajouter un cas, cliquez sur le **Ajouter nouveau cas** bouton en bas de **commutateur\<T >** concepteur. Le bouton se transforme en zone de texte (zone de liste déroulante si le type générique sélectionné lors de l’ajout du commutateur\<T > est String ou Enum). Après l’ajout d’une clé dans le **cas valeur** zone, la zone de cas se développe et une activité peut être déposée où le texte d’indication « Déposer l’activité ici » pour définir la logique d’exécution pour le cas.|  
  
 Plusieurs cas peuvent être ajoutés tant que les clés de cas ne sont pas dupliquées. Sinon, une boîte de dialogue d'erreur s'affiche pour signaler que la clé de cas spécifiée existe déjà et que vous devez en choisir une autre. Dans le **commutateur\<T >** concepteur, qu’une seule zone de cas peut être développée à la fois. Si une zone de cas est affiché en mode réduit, cliquez dessus pour la développer. Notez que lorsqu'un cas est affiché en mode réduit, le concepteur place le nom d'affichage de l'activité (si elle existe) à l'intérieur du cas, à droite. Sinon, elle est affichée la **ajouter une activité** bouton qui développe le cas si vous cliquez dessus et vous permet d’ajouter une activité.  
  
 Cliquer sur la clé d'un cas existant transforme l'apparence de cette dernière d'étiquette en zone de texte afin que vous puissiez la modifier.  
  
 Vous disposez de 2 méthodes pour supprimer un cas :  
  
1. Sélectionnez le cas et supprimez-le.  
  
2. Sélectionnez le cas, avec le bouton droit pour afficher le menu contextuel et sélectionnez **supprimer**.  
  
   Notez que vous devez sélectionner le cas lui-même pour le supprimer. La sélection et la suppression de l'activité à l'intérieur d'un cas supprime uniquement l'activité mais pas le cas.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
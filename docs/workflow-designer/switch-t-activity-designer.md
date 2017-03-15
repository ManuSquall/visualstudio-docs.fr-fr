---
title: "Concepteur d&#39;activit&#233;s Switch&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.ModelItemKeyValuePair.UI"
  - "System.Activities.Statements.Switch`1.UI"
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Concepteur d&#39;activit&#233;s Switch&lt;T&gt;
L'activité <xref:System.Activities.Statements.Switch%601> évalue une expression spécifiée et exécute l'activité à partir d'une collection d'activités dont la clé associée correspond à la valeur obtenue de l'évaluation.  
  
 Le concepteur d'activités **Switch\<T\>** permet de créer et configurer une activité <xref:System.Activities.Statements.Switch%601> dans [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## Activité Switch\<T\>  
 Une activité <xref:System.Activities.Statements.Switch%601> contient une propriété <xref:System.Activities.Statements.Switch%601.Expression%2A> et un dictionnaire de propriétés <xref:System.Activities.Statements.Switch%601.Cases%2A>.Chaque cas dans le dictionnaire est composé d'une paire qui contient un paramètre *key* et une activité qui lui sert de paramètre *value*.L'activité <xref:System.Activities.Statements.Switch%601> évalue la propriété <xref:System.Activities.Statements.Switch%601.Expression%2A> et la compare à chacune des clés.Si une correspondance est trouvée, l'activité correspondante est exécutée.Une seule correspondance est possible, car les clés de dictionnaire doivent être uniques par rapport au type d'égalité défini par le comparateur d'égalité du dictionnaire.Si aucune correspondance n'est trouvée, l'activité <xref:System.Activities.Statements.Switch%601.Default%2A> est exécutée.  
  
## Comment utiliser le concepteur d'activités Switch\<T\>  
 Le concepteur d'activités **Switch\<T\>** se trouve dans la catégorie **Flux de contrôle** de la **boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\). Une fois déposé dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], il affiche la boîte de dialogue **Sélectionner les types** pour permettre à l'utilisateur de spécifier le type *T* générique utilisé dans l'activité <xref:System.Activities.Statements.Switch%601>.La valeur par défaut est **Int32**.Une fois que le type *T* générique a été sélectionné, un concepteur **Switch\<T\>** est ajouté dans Workflow Designer.  
  
 Les propriétés du concepteur **Switch\<T\>** sont présentées ci\-dessous.Toutes ces propriétés peuvent être modifiées dans la grille des propriétés.Certaines peuvent également être modifiées dans l'aire du concepteur.  
  
 Le tableau suivant répertorie les propriétés de l'activité <xref:System.Activities.Statements.Switch%601> qui sont les plus utiles et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Switch%601>.La valeur par défaut est Switch\<Int32\>.La valeur peut être modifiée dans la fenêtre **Propriétés** ou directement dans l'en\-tête du concepteur.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Spécifie l'expression à comparer aux clés dans la collection de cas pour déterminer le cas à exécuter.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Spécifie l'activité exécutée si aucune correspondance n'est trouvée.Cliquez sur le bouton **Ajouter une activité** dans le concepteur pour ouvrir la zone **Par défaut** dans laquelle l'activité peut être déposée.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Spécifie les cas à évaluer.Pour ajouter un cas, cliquez sur le bouton **Ajouter un nouveau cas** en bas du concepteur **Switch\<T\>**.Le bouton se transforme en zone de texte \(ou en zone de liste déroulante si le type générique sélectionné lors de l'ajout du Switch\<T\> est String ou Enum\).Après l'ajout d'une clé dans la zone **Valeur associée au cas**, la zone de cas se développe et une activité peut être déposée à l'emplacement du texte de l'indication « Déposer l'activité ici » pour définir la logique d'exécution du cas.|  
  
 Plusieurs cas peuvent être ajoutés tant que les clés de cas ne sont pas dupliquées.Sinon, une boîte de dialogue d'erreur s'affiche pour signaler que la clé de cas spécifiée existe déjà et que vous devez en choisir une autre.Dans le concepteur **Switch\<T\>**, une seule zone de cas peut être développée à la fois.Si une zone de cas est affiché en mode réduit, cliquez dessus pour la développer.Notez que lorsqu'un cas est affiché en mode réduit, le concepteur place le nom d'affichage de l'activité \(si elle existe\) à l'intérieur du cas, à droite.Sinon, il affiche le bouton **Ajouter une activité** qui développe le cas si vous cliquez dessus et qui vous permet d'ajouter une activité.  
  
 Cliquer sur la clé d'un cas existant transforme l'apparence de cette dernière d'étiquette en zone de texte afin que vous puissiez la modifier.  
  
 Vous disposez de 2 méthodes pour supprimer un cas :  
  
1.  Sélectionnez le cas et supprimez\-le.  
  
2.  Sélectionnez le cas, cliquez avec le bouton droit pour afficher le menu contextuel, puis sélectionnez **Supprimer**.  
  
 Notez que vous devez sélectionner le cas lui\-même pour le supprimer.La sélection et la suppression de l'activité à l'intérieur d'un cas supprime uniquement l'activité mais pas le cas.  
  
## Voir aussi  
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
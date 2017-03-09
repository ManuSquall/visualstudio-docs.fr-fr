---
title: "Concepteur d&#39;activit&#233;s TryCatch | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TryCatch.UI"
  - "System.Activities.Statements.Catch`1.UI"
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Concepteur d&#39;activit&#233;s TryCatch
Le concepteur d'activités **TryCatch** permet de créer et configurer une activité <xref:System.Activities.Statements.TryCatch>.  
  
## Activité TryCatch  
 L'activité <xref:System.Activities.Statements.TryCatch> contient une activité <xref:System.Activities.Statements.TryCatch.Try%2A>, une collection de **Catch\<TException\>** et une activité <xref:System.Activities.Statements.TryCatch.Finally%2A>.Un objet <xref:System.Activities.Statements.Catch%601> de type **TException** contient une propriété <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> et une propriété <xref:System.Activities.Statements.Catch%601.Action%2A>.Ensemble, ils permettent d'implémenter un mécanisme classique de gestion des erreurs basé sur les exceptions.Une activité <xref:System.Activities.Statements.TryCatch> essaie d'exécuter son activité <xref:System.Activities.Statements.TryCatch.Try%2A>.Si l'activité <xref:System.Activities.Statements.TryCatch.Try%2A> lève une exception, l'activité <xref:System.Activities.Statements.TryCatch> utilise sa collection **Catch\<TException\>** pour établir une correspondance avec l'exception.S'il existe une correspondance, la propriété <xref:System.Activities.Statements.Catch%601.Action%2A> du **Catch\<TException\>** correspondant est alors exécutée, en servant de logique de gestion des erreurs pour l'exception.Si les activités de la section <xref:System.Activities.Statements.TryCatch.Try%2A> s'achèvent correctement ou les activités de <xref:System.Activities.Statements.TryCatch.Catches%2A> s'achèvent correctement, l'activité <xref:System.Activities.Statements.TryCatch> exécute son activité <xref:System.Activities.Statements.TryCatch.Finally%2A>.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Exceptions](../Topic/Exceptions.md).  
  
### Utilisation du concepteur d'activités TryCatch  
 Le concepteur d'activités **TryCatch** se trouve dans la catégorie **Gestion des erreurs** de la **boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** à gauche de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **TryCatch** peut être déplacé de la **boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette opération crée une activité <xref:System.Activities.Statements.TryCatch> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut TryCatch.La valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **TryCatch** ou dans la zone **DisplayName** de la grille des propriétés.Les autres propriétés doivent être modifiées dans l'aire du concepteur d'activités **TryCatch**.  
  
 Cliquez sur le bouton Développer dans le coin supérieur droit du concepteur **TryCatch** pour afficher les zones **Try**, **Catches** et **Finally** dans la vue développée.Pour ajouter un catch, cliquez sur le bouton **Ajouter un nouveau catch** dans le concepteur **TryCatch**.Le bouton se transforme en zone de liste déroulante Type.Sélectionnez un type d'exception et appuyez sur ENTRÉE pour ajouter le catch.Après l'ajout d'un élément **Catch**, la zone de catch se développe et une activité peut y être déposée pour définir la logique d'exécution du catch.Notez la présence d'une zone de texte à droite de la zone de catch développée.Vous pouvez nommer la variable d'exception à l'aide de cette zone de texte.La variable d'exception peut être utilisée uniquement pour les activités situées dans le même **Catch**.  
  
 Le concepteur **TryCatch** ne prend pas en charge la modification du **Catch**.Si vous souhaitez modifier le type d'exception, vous devez supprimer le **Catch** et en ajouter un nouveau.Pour supprimer un **Catch**, sélectionnez\-le puis supprimez\-le, ou cliquez sur **Supprimer** dans le menu contextuel accessible par un clic droit.  
  
### Propriétés TryCatch  
 Le tableau suivant affiche les propriétés <xref:System.Activities.Statements.TryCatch> et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.TryCatch>.TryCatch est la valeur par défaut.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Première activité exécutée lorsque <xref:System.Activities.Statements.TryCatch> s'exécute.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Collection d'éléments **Catch** à vérifier lorsque l'activité <xref:System.Activities.Statements.TryCatch.Try%2A> lève une exception.<br /><br /> Vous devez au moins ajouter une activité dans <xref:System.Activities.Statements.TryCatch.Catches%2A> ou une activité dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Activité à exécuter lorsque l'exécution de <xref:System.Activities.Statements.TryCatch.Try%2A> et de toutes les activités nécessaires de la collection <xref:System.Activities.Statements.TryCatch.Catches%2A> est terminée.<br /><br /> Vous devez au moins ajouter une activité dans <xref:System.Activities.Statements.TryCatch.Catches%2A> ou une activité dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
  
## Voir aussi  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)
---
title: "Concepteur d&#39;activit&#233;s ForEach&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ForEach`1.UI"
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Concepteur d&#39;activit&#233;s ForEach&lt;T&gt;
L'activité <xref:System.Activities.Statements.ForEach%601> exécute l'activité contenue dans sa propriété <xref:System.Activities.Statements.ForEach%601.Body%2A> pour chaque élément d'une collection <xref:System.Activities.Statements.ForEach%601.Values%2A> spécifiée.  
  
## Propriétés de ForEach\<T\> dans Workflow Designer  
 Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.ForEach%601> et décrit comment les utiliser dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------------|-----------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.ForEach%601>.ForEach\<Int32\>. est la valeur par défaut.Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Collection d'éléments à itérer.Pour définir la propriété <xref:System.Activities.Statements.ForEach%601.Values%2A>, tapez une expression [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] dans la zone **Valeurs** sur le concepteur d'activités **ForEach\<T\>** ou dans la grille des propriétés.|  
|*TypeArgument*|True|Type des éléments de la collection <xref:System.Activities.Statements.ForEach%601.Values%2A> spécifié par le paramètre générique *T*.Par défaut, *TypeArgument* a la valeur **Int32**.Pour modifier le type, modifiez la zone de liste déroulante *TypeArgument* de la grille des propriétés.|  
  
 Par défaut, l'itérateur de boucle est nommé **item**.Vous pouvez modifier le nom de la variable d'itérateur dans le concepteur d'activités <xref:System.Activities.Statements.ForEach%601>.L'itérateur de boucle peut être utilisé dans des expressions dans les enfants de l'activité <xref:System.Activities.Statements.ForEach%601>.  
  
## Voir aussi  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
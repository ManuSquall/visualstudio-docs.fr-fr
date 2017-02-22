---
title: "Concepteur d&#39;activit&#233;s InvokeMethod | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.InvokeMethod.UI"
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Concepteur d&#39;activit&#233;s InvokeMethod
Le concepteur **InvokeMethod** permet de créer et configurer une activité <xref:System.Activities.Statements.InvokeMethod>.  
  
## Activité InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> appelle une méthode publique d'un objet ou d'un type spécifié.  
  
### Utilisation du concepteur d'activités InvokeMethod  
 Le concepteur d'activités **InvokeMethod** se trouve dans la catégorie **Primitives** de la **boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **InvokeMethod** peut être déplacé de la **boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette opération crée une activité <xref:System.Activities.Statements.InvokeMethod> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut InvokeMethod.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **InvokeMethod** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés InvokeMethod  
 Le tableau suivant présente les propriétés <xref:System.Activities.Statements.InvokeMethod> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------------|-----------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.InvokeMethod>.La valeur par défaut est InvokeMethod.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Nom de la méthode à appeler lorsque l'activité s'exécute.La méthode appelée doit être déclarée comme **public**.Cette propriété peut être modifiée dans l'aire du concepteur.Il s'agit d'une propriété obligatoire.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Collection de paramètres de la méthode appelée.Les paramètres doivent être ajoutés à la collection dans l'ordre dans lequel ils s'affichent dans la signature de méthode.Dans la grille des propriétés, cliquez sur le bouton de sélection dans le champ **Paramètres**, la boîte de dialogue **Paramètres** s'affiche pour vous permettre de définir cette propriété.Cliquez sur le bouton **Créer un argument** pour ajouter les paramètres.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Valeur de retour de l'appel de méthode.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Spécifie si la méthode est appelée de façon asynchrone.La valeur par défaut est **False**.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Objet qui contient la méthode à appeler.Cette propriété peut être modifiée dans l'aire du concepteur.<br /><br /> La propriété <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> ou <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> doit obligatoirement être définie.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Type de <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.Cette propriété peut être modifiée dans l'aire du concepteur.Elle doit être définie uniquement si la méthode appelée est statique.|  
  
 Pour passer des paramètres en tant que paramètre **out** C\# \(par exemple, `Method1(out myParam)),` vous devez utiliser **OutArgument** au lieu de **InOutArgument**.  
  
 Les méthodes comportant des arguments appelés **TargetObject** ou **Result** ne peuvent pas être appelées à l'aide de l'activité <xref:System.Activities.Statements.InvokeMethod>.En effet, l'activité <xref:System.Activities.Statements.InvokeMethod> inscrit <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> et <xref:System.Activities.Statements.InvokeMethod.Result%2A> dans <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
 L'algorithme permettant d'inscrire les paramètres dans <xref:System.Activities.Activity.CacheMetadata%2A> est présenté dans la liste suivante :  
  
1.  Inscrivez l'argument <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.  
  
2.  Inscrivez l'argument <xref:System.Activities.Statements.InvokeMethod.Result%2A>.  
  
3.  Effectuez une itération au sein de la collection <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> et inscrivez chaque argument.  
  
 L'exception obtenue est de type <xref:System.Activities.InvalidWorkflowException> avec le message suivant : 'InvokeMethod' : Une variable, un RuntimeArgument ou un DelegateArgument, portant le nom 'TargetObject' existe déjà.Les noms doivent être uniques au sein de la portée de l'environnement.  
  
 Cette restriction ne s'applique pas à <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> et <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>, car il ne s'agit pas d'arguments de flux de travail et ils ne sont donc pas inscrits dans la collection <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> de l'activité <xref:System.Activities.Statements.InvokeMethod> dans méthode <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
## Voir aussi  
 [Primitives](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)
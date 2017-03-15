---
title: "D&#233;pannage des exceptions&#160;: System.Data.ConstraintException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ConstraintException (classe)"
ms.assetid: 5e9ba3b8-73d5-4657-a76e-63ab6ea32cf1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Data.ConstraintException
Une exception <xref:System.Data.ConstraintException> est levée lorsque l'action entreprise ne respecte pas une contrainte.  
  
## Conseils associés  
 **Assouplissez ou désactivez les contraintes dans votre DataSet.**.  
 Vous pouvez utiliser la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> pour désactiver temporairement les contraintes pendant le remplissage des tables dans un objet <xref:System.Data.DataSet>.  
  
 **Assurez\-vous que vous ne tentez pas d'assigner une valeur à un champ clé primaire dont la clé primaire existe déjà dans la table de données.**  
 Si la clé primaire existe déjà, cette exception est levée.  
  
 **Effacez les groupes de données avant de les charger à partir de l'état d'affichage.**  
 Si le groupe de données contient des données lors de son chargement, cette exception peut être levée.  
  
## Voir aussi  
 <xref:System.Data.ConstraintException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)
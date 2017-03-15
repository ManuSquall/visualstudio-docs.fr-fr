---
title: "Le param&#232;tre &#39;Set&#39; doit &#234;tre du m&#234;me type que la propri&#233;t&#233; conteneur | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31064"
  - "bc31064"
helpviewer_keywords: 
  - "BC31064"
ms.assetid: f0b8310d-68a1-4989-ac64-03b1861528ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre &#39;Set&#39; doit &#234;tre du m&#234;me type que la propri&#233;t&#233; conteneur
Le type du paramètre de la procédure de propriété `Set` est différent de la propriété à laquelle ce paramètre appartient.  
  
 **ID d’erreur :** BC31064  
  
### Pour corriger cette erreur  
  
-   Attribuez la valeur `Set` au type de données du paramètre de sorte qu’il corresponde au type de données de la propriété. Exemple :  
  
    ```  
    Class Class1 ' Declare a local variable to hold the property value. Private Fval As Integer Property F() As Integer Get Return Fval End Get Set(ByVal Value As Integer) Fval = Value End Set End Property End Class  
    ```  
  
## Voir aussi  
 [NOT IN BUILD : Comment : ajouter des champs et des propriétés à une classe](http://msdn.microsoft.com/fr-fr/ae53f61b-3abc-413e-8931-703c5f5e8fc2)   
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [NOT IN BUILD : Propriétés et procédures de propriétés](http://msdn.microsoft.com/fr-fr/23e2a1ec-7e9d-4109-8940-c703d981077b)
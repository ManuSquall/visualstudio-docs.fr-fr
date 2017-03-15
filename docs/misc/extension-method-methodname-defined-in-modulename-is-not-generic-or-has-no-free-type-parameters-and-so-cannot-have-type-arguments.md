---
title: "La m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_module&gt;&#39; n’est pas g&#233;n&#233;rique (ou n’a pas de param&#232;tre de type libre) et ne peut pas avoir d’arguments de type | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36907"
  - "vbc36907"
helpviewer_keywords: 
  - "BC36907"
ms.assetid: 45191e93-89d1-48ec-99a5-ff9661a2a6ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_module&gt;&#39; n’est pas g&#233;n&#233;rique (ou n’a pas de param&#232;tre de type libre) et ne peut pas avoir d’arguments de type
Un argument de type a été spécifié dans un appel à une méthode d’extension qui n’a aucun paramètre générique ou n’a aucun paramètre générique pour lequel un type n’est pas encore spécifié. Par exemple, le code suivant génère cette erreur.  
  
```vb#  
' The extension method is not generic. <Extension()> _ Sub Example(ByVal str As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
Dim str = "hi" '' The call to Example specifies a type argument. '' Not valid. 'str.Example(Of String)()  
```  
  
 **ID d’erreur :** BC36907  
  
### Pour corriger cette erreur  
  
-   Ajoutez un paramètre de type à la définition de méthode d’extension.  
  
-   Supprimez l’argument de type supplémentaire de l’appel de procédure.  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)
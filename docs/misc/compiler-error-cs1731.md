---
title: "Erreur du compilateur CS1731 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1731"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1731"
ms.assetid: 267b32aa-a692-4a54-8654-0540ee36c0a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1731
Impossible de convertir 'expression' en délégué, car certains types de retour du bloc ne sont pas implicitement convertibles en type de retour délégué.  
  
 Cette erreur est générée quand le type de retour d’une expression lambda ou d’une méthode anonyme n’est pas compatible avec le type de retour du délégué.  
  
### Pour corriger cette erreur  
  
1.  Modifiez le type de retour du délégué ou de l’expression.  
  
## Exemple  
 Le code suivant génère l’erreur CS1731 :  
  
```  
class CS1731 { delegate double D(); D d = () => { return "Who knows the real sword of Gryffindor?"; }; }  
```
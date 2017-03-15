---
title: "Num&#233;ro d&#39;enregistrement incorrect | Microsoft Docs"
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
  - "vbrID63"
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Num&#233;ro d&#39;enregistrement incorrect
Le numéro d’enregistrement dans une instruction `a FileGet`, `FilePut`, `FileGetObject` ou `FilePutObject` est inférieur ou égal à zéro.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez les calculs utilisés pour générer le numéro d’enregistrement. Vérifiez l’orthographe des variables contenant le numéro d’enregistrement ou utilisées dans le calcul des numéros d’enregistrement. Un nom de variable mal orthographié est déclaré implicitement et possède une valeur égale à zéro, sauf si vous avez utilisé `Option Explicit On` dans le module.  
  
## Voir aussi  
 [Option Explicit Statement](/dotnet/visual-basic/language-reference/statements/option-explicit-statement)
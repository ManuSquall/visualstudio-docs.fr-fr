---
title: "Avertissement de ligne de commande D9042 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "D9042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9042"
ms.assetid: d710693b-e422-40b2-b2dd-79e1b163b9e6
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de ligne de commande D9042
valeur 'valeur' non valide pour '\/option' ; 'valeur' pris par défaut ; les avertissements liés à l’analyse du code ne sont pas disponibles dans cette édition du compilateur  
  
 Un numéro d’avertissement d’analyse du code a été ajouté à l’option de ligne de commande **\/wd**, **\/we**, **\/wo** ou **\/wl** et l’option de ligne de commande **\/analyze** a été spécifiée sur une plateforme qui ne prend pas en charge l’analyse du code. Pour résoudre cet avertissement, passez à la version x86 de Visual Studio Team System ou supprimez l’option de ligne de commande **\/analyze**.  
  
## Exemple  
 L’exemple de ligne de commande suivant génère l’avertissement D9042 sur un système x64 ou Itanium :  
  
```  
cl /EHsc /LD /wd6001 /analyze filename.cpp  
```  
  
 Pour résoudre cet avertissement, passez à la version x86 de Visual Studio Team System ou supprimez les options de ligne de commande **\/analyze** et **\/wd6001**.  
  
## Voir aussi  
 [Erreurs de ligne de commande D8000 à D9999](/visual-cpp/error-messages/tool-errors/command-line-errors-d8000-through-d9999)   
 [Options du compilateur](/visual-cpp/build/reference/compiler-options)
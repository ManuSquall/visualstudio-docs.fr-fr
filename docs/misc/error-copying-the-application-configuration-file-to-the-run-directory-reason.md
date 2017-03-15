---
title: "Error copying the application configuration file to the run directory. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cant_copy_appcfg_file"
ms.assetid: 15699a76-16ef-40a8-8ed4-5eef4d2c0e72
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error copying the application configuration file to the run directory. &lt;reason&gt;
Le système de projet ne peut pas copier un fichier app.config dans le répertoire à partir duquel le projet est exécuté.  Le processus de génération échoue si cette erreur se produit.  
  
 Cette erreur ne se produit que lors de la génération d'un fichier .exe.  
  
 Le système de génération tente de trouver un fichier nommé app.config dans le dossier racine du projet.  Ce fichier est ensuite copié dans le répertoire de sortie du projet et est nommé *FichierSortie.*config.  
  
 Les raisons de cette erreur sont notamment les suivantes :  
  
-   manque d'espace disque ;  
  
-   dépassement de la limite MAX\_PATH.  
  
 Vous pouvez également vérifier qu'il n'existe pas d'autre copie de l'application en exécution.  
  
## Voir aussi  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
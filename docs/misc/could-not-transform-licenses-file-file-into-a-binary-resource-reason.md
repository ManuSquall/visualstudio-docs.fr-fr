---
title: "Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.licx_generator_failed"
ms.assetid: 875e948c-d7a3-4ffc-be0d-f341de5f6310
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt;
Le processeur de licences utilisé pour transformer les fichiers .licx en ressources binaires a échoué pour une raison quelconque.  
  
 Cette erreur est généralement causée par un fichier .licx incorrect.  Il se peut par exemple que le fichier ait été ouvert et modifié dans un éditeur de texte.  
  
 Le processus de génération échoue si cette erreur se produit.  
  
### Pour corriger cette erreur  
  
1.  Sélectionnez le projet dans l'Explorateur de solutions.  
  
2.  Dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.  
  
3.  Dans l'Explorateur de solutions, développez le dossier obj, puis développez le dossier **Déboguer**.  
  
4.  Repérez le fichier nommé "MonApplication.exe.licenses" où MonApplication est le nom de votre application Windows Forms.  
  
5.  Supprimez ce fichier et régénérez la solution.  
  
## Voir aussi  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)
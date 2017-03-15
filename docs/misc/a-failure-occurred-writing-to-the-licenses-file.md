---
title: "A failure occurred writing to the licenses file | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.fail_writing_licenses_file"
ms.assetid: 7ea1e2ac-fc94-4d53-8ce9-2ae31bcba85d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# A failure occurred writing to the licenses file
Le système de projet n'a pas pu écrire dans le fichier transformé.  Dans le cadre de la préparation des licences, le système de projet transformera les fichiers texte .licx en fichiers de licences binaires interprétables par le système de licences [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Les raisons possibles de cette erreur sont notamment un manque d'espace disque sur le périphérique ou le dépassement de la limite MAX\_PATH pour les noms de fichiers.  
  
 **Pour corriger cette erreur**  
  
-   Déplacez le projet vers un dossier différent doté d'un nom de chemin d'accès absolu court ou raccourcissez le nom du fichier de sortie.  
  
     Le processus de génération échoue si cette erreur se produit.  
  
## Voir aussi  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)
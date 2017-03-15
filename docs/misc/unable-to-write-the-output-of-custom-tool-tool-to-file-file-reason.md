---
title: "Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_write_gen_output"
ms.assetid: eafcee9e-186b-4019-9042-8d8f9fc0925a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt;
Le système de projet n'a pas pu écrire la sortie de l'outil personnalisé dans le fichier spécifié.  
  
 À condition que le nom de fichier de l'entrée d'un outil personnalisé demeure inchangé, la sortie d'un outil personnalisé est écrite dans le même fichier.  Cette erreur se produit si la sortie générée est verrouillée sur le disque.  
  
 **Pour corriger cette erreur**  
  
-   Redémarrez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et réexécutez l'outil personnalisé en cliquant avec le bouton droit sur le fichier affecté et en sélectionnant **Exécuter un outil personnalisé** dans le menu contextuel.  
  
     Le fichier généré est probablement obsolète car le système de projet n'a pas pu le mettre à jour.
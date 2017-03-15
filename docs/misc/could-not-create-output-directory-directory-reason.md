---
title: "Could not create output directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_create_output_dir"
ms.assetid: b4d1d19f-f582-49d0-a9a9-d3f4ce0a447b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not create output directory &#39;directory&#39;. &lt;reason&gt;
Le système de projet n'a pas pu créer de répertoire du projet.  
  
 Le système de projet tentera de créer tous les répertoires de sortie dès que le projet sera ouvert.  Vous trouverez ci\-dessous une liste des répertoires de sortie créés par le système de projet :  
  
 *DossierProjet*\\obj\\`configname`  
 Répertoire temporaire de sortie spécifique à la configuration.  
  
 *DossierProjet*\\obj\\`configname`\\temp  
 Zone de travail utilisée par le compilateur.  
  
 *DossierProjet*\\obj\\`configname`\\temppe  
 Les assemblys temporaires utilisés par les concepteurs au moment du design sont créés à cet endroit.  
  
 outputdir  
 Répertoire spécifié par la propriété de chemin de sortie.  Pour plus d'informations, consultez [Générer, page du Concepteur de projets \(C\#\)](../ide/reference/build-page-project-designer-csharp.md).  
  
 La raison la plus courante de l'échec de création d'un des répertoires sous le dossier obj est le dépassement de la limite MAX\_PATH pour les noms de répertoires.  
  
 Les raisons moins courantes sont notamment une autorisation refusée et un manque d'espace disque.  
  
 **Pour corriger cette erreur**  
  
-   Si le chemin d'accès est trop long, changez l'emplacement du projet ou raccourcissez le nom de la configuration de projet.  
  
     Le processus de génération échoue si cette erreur se produit.  
  
## Voir aussi  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
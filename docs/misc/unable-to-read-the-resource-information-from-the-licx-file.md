---
title: "Unable to read the resource information from the licx file | Microsoft Docs"
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
  - "vs.tasklisterror.fail_reading_licx_file"
ms.assetid: e59f0965-fa1c-4852-bd39-63430d5b7d9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to read the resource information from the licx file
Le fichier .licx n'a pas pu être lu par le système de projet.  Dans le cadre de la préparation des licences, le système de projet transforme des fichiers texte .licx en fichiers de ressources binaires qui conviennent à une utilisation avec le modèle de licences COM\+.  
  
 Le fichier .licx est automatiquement généré ou mis à jour par le concepteur Windows Forms lorsqu'un contrôle sous licence est ajouté au formulaire.  Il existe un fichier .licx par projet. Il se trouve toujours dans le dossier racine et est toujours nommé Licenses.licx.  
  
 Certaines raisons de cette erreur sont notamment les suivantes :  
  
-   autorisation refusée ;  
  
-   perte de la communication avec le serveur Web pour les projets Web.  
  
 Le processus de génération échoue si cette erreur se produit.  
  
## Voir aussi  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)
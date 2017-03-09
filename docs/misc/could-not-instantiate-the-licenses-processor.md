---
title: "Could not instantiate the licenses processor | Microsoft Docs"
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
  - "vs.tasklisterror.no_licx_generator"
ms.assetid: 9e95d590-f41f-4cfa-bc73-fadeacfdb879
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not instantiate the licenses processor
L'outil utilisé pour transformer les fichiers .licx en ressources binaires n'a pas pu être instancié.  
  
 Dans le cadre de la compilation, le système de projet transforme un fichier texte .licx en ressource binaire qui assure la prise en charge des licences de contrôles .NET.  La ressource binaire est ensuite incorporée dans la sortie de projet.  
  
 Le processus de génération échoue si cette erreur se produit.  
  
 Le fichier .licx est automatiquement généré ou mis à jour par le concepteur Windows Forms lorsqu'un contrôle sous licence est ajouté au formulaire.  Il existe un fichier .licx par projet. Il se trouve toujours dans le dossier racine et est toujours nommé Licenses.licx.  
  
 **Pour corriger cette erreur**  
  
-   Réinstallez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Voir aussi  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)
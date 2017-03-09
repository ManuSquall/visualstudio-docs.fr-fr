---
title: "Invalid assembly strong name or name not specified | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.invalid_strong_name"
ms.assetid: cb02b69d-09a9-478f-914c-fbdc420e973d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Invalid assembly strong name or name not specified
La propriété de projet du modèle objet du système de projet qui vous permet de spécifier un nom de clé ou un conteneur clé pour les projets qui seront générés en assemblys avec un nom fort \(assembly signé\) était vide.  Si ce message est affiché, la génération ne réussit pas.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez qu'un nom de conteneur clé ou un fichier de clé est spécifié dans le code.  
  
## Voir aussi  
 [Création et utilisation d'assemblys avec nom fort](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)
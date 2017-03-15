---
title: "Warning: Found conflicts between different versions of the same dependent assembly | Microsoft Docs"
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
  - "ResolveAssemblyReference.SuggestedRedirects"
ms.assetid: fd14a789-bbdf-46c7-bcd3-9d3165adf96d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Warning: Found conflicts between different versions of the same dependent assembly
Cet avertissement affiche si le graphique de dépendance de votre projet contient des références aux différentes versions du même assembly.  
  
 Si vous utilisez un fichier app.config, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous permet d'ajouter à celui\-ci une redirection de liaison.  Une redirection de liaison force toutes les références d'assembly à procéder à une redirection vers la version de l'assembly ayant le numéro le plus élevé. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enregistre les informations de redirection dans app.config.  Si vous utilisez une redirection de liaison, cet avertissement n'apparaît plus.  
  
 Si vous décidez de ne pas ajouter de redirection de liaison, votre projet continue à référencer la même version de l'assembly comme il l'a fait auparavant.  Toutefois, cet avertissement continue à apparaître.  
  
### Pour corriger cette erreur  
  
-   Double\-cliquez sur l'avertissement puis sélectionnez « Oui » lorsque vous obtenez l'invite, « est\-ce que vous souhaitez résoudre ces conflits en ajoutant un enregistrement de redirection de liaison dans le fichier app.config ? ».
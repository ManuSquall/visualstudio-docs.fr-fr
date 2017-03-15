---
title: "The custom tool &#39;custom tool&#39; failed. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.generator_fail_errorinfo"
ms.assetid: e846b946-a123-49fe-b4bc-a7bbda501417
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The custom tool &#39;custom tool&#39; failed. &lt;reason&gt;
L'outil personnalisé ne s'est pas exécuté correctement.  
  
 Si vous rencontrez une erreur MSDataSetGenerator lors de la mise à jour des projets qui contiennent des groupes de données multicouches, vous devez réexécuter l'outil personnalisé après la mise à jour de tous les projets.  
  
 L'outil personnalisé MSDataSetGenerator a échoué.  Le projet spécifié dans l'attribut DataSetProject de \<nom du groupe de données\> doit cibler une version du .NET Framework équivalente ou ultérieure à celle du projet actuel.  
  
### Pour corriger les erreurs MSDataSetGenerator survenues dans les groupes de données multicouches  
  
-   Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le fichier .xsd, puis cliquez sur **Exécuter un outil personnalisé**.
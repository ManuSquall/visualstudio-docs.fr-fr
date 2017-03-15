---
title: "Avertissement&#160;: code p&#233;rim&#233;, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.ENC.stalecode"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Avertissement : code périmé (boîte de dialogue)"
  - "code, avertissement relatif au code périmé"
  - "avertissements, boîte de dialogue Avertissement : code périmé"
  - "Modifier et continuer, code périmé"
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Avertissement&#160;: code p&#233;rim&#233;, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue s'affiche lorsque vous avez effectué des modifications au code natif que la fonction **Modifier & Continuer** n'a pas pu appliquer immédiatement.  Par conséquent, une partie du code natif du frame de pile actif n'est plus à jour ; il est périmé.  Pour plus d'informations, consultez [How to: Work with Stale Code](http://msdn.microsoft.com/fr-fr/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **Ne plus afficher cette boîte de dialogue**  
 Si vous activez cette case à cocher, Modifier & Continuer appliquera à l'avenir les modifications de code sans vous en demander l'autorisation.  Vous pouvez réactiver cet avertissement à partir de la boîte de dialogue **Options** : dans le dossier **Débogage**, cliquez sur la page **Modifier & Continuer**, puis activez la case à cocher **Signaler le code périmé**.  
  
## Voir aussi  
 [Limitations et modifications de code prises en charge \(C\+\+\)](../debugger/supported-code-changes-cpp.md)   
 [Modifier & Continuer, Débogage, boîte de dialogue Options](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)
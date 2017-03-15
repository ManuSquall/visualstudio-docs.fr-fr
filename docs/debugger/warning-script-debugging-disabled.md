---
title: "Avertissement&#160;: le d&#233;bogage de script est d&#233;sactiv&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.scriptdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Avertissement&#160;: le d&#233;bogage de script est d&#233;sactiv&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le débogage de script est actuellement désactivé dans Internet Explorer  
  
 Ce message d'avertissement s'affiche lorsque vous essayez de déboguer le script sans activer le débogage de script dans Internet Explorer.  Pour des raisons de sécurité, Internet Explorer désactive le débogage de script par défaut.  
  
### Pour activer le débogage de script dans Internet Explorer  
  
1.  Dans le menu  **Outils** d'Internet Explorer, sélectionnez **Options Internet**.  
  
2.  Dans la boîte de dialogue **Options Internet**, cliquez sur l'onglet **Avancées**.  
  
3.  Sous l'onglet **Avancés**, consultez la zone **Paramètres**, catégorie **Navigation**.  
  
4.  Désactivez la case à cocher **Désactiver le débogage des scripts \(Internet Explorer\)**.  
  
5.  Cliquez sur **OK**.  
  
6.  Quittez, puis redémarrez Internet Explorer.  
  
     Les nouveaux paramètres sont désormais appliqués.  
  
## Voir aussi  
 [Comment : attacher à un script](../debugger/how-to-attach-to-script.md)
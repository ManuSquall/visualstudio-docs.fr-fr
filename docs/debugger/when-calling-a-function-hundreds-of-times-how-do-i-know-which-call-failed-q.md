---
title: "Lorsque j&#39;appelle une fonction des centaines de fois, comment puis-je savoir quel appel a &#233;chou&#233;&#160;? | Microsoft Docs"
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
  - "vs.debug.functions"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "points d'arrêt, dépanner"
  - "points d'arrêt conditionnels"
  - "erreurs (débogueur), rechercher l'appel de fonction qui a échoué"
  - "erreurs (débogueur), appels de fonction"
  - "erreurs (Visual Studio), appels de fonction"
  - "échecs"
  - "appels de fonction, échec"
  - "fonctions (débogueur)"
  - "nombres d'accès"
  - "échecs des appels au point d'arrêt d'emplacement"
  - "Skip Count"
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Lorsque j&#39;appelle une fonction des centaines de fois, comment puis-je savoir quel appel a &#233;chou&#233;&#160;?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Description du problème  
 Mon programme échoue lors de l'appel à une certaine fonction, `CnvtV`.  Mais cet échec survient probablement après plusieurs centaines d'appels à la fonction par le programme.  Si je définis un point d'arrêt d'emplacement sur `CnvtV`, le programme s'arrête à chaque appel de cette fonction, ce que je veux éviter.  J'ignore quelles conditions ont provoqué l'échec de l'appel et je ne peux donc pas définir un point d'arrêt conditionnel.  Que puis\-je faire ?  
  
## Solution  
 Vous pouvez définir un point d'arrêt sur la fonction en affectant au champ **Nombre d'accès** une valeur très élevée que vous ne risquez pas d'atteindre.  Dans le cas présent, vous estimez que la fonction `CnvtV` est appelée plusieurs centaines de fois ; vous affectez par conséquent à **Nombre d'accès** la valeur 1000 ou une valeur supérieure.  Exécutez ensuite le programme et patientez jusqu'à l'échec de l'appel.  Lorsqu'il échoue, ouvrez la fenêtre Points d'arrêt et examinez la liste des points d'arrêt.  Le point d'arrêt que vous avez défini sur `CnvtV` apparaît, suivi du nombre d'accès et du nombre d'itérations restantes :  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Vous savez à présent que la fonction a échoué au 101e appel.  Si vous réinitialisez le point d'arrêt avec un nombre d'accès égal à 101, puis que vous réexécutez le programme, ce dernier s'arrête au niveau de l'appel à `CnvtV` qui a provoqué son échec.  
  
## Voir aussi  
 [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Setting Breakpoints](http://msdn.microsoft.com/fr-fr/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
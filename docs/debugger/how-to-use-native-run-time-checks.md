---
title: "Comment&#160;: utiliser les contr&#244;les natifs &#224; l&#39;ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime.errorchecks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/O (option du compilateur), /RTC (option)"
  - "/RTC (option du compilateur C++), /O (option du compilateur)"
  - "tableaux (Visual Studio), débogage"
  - "débogueur, contrôles natifs à l'exécution"
  - "débogueur, erreurs d'exécution"
  - "déboguer des tableaux"
  - "contrôles natifs à l'exécution"
  - "O (option du compilateur), /RTC (option)"
  - "option de génération optimisée"
  - "RTC (option du compilateur), /O (option du compilateur)"
  - "vérifications à l'exécution"
  - "vérifications à l'exécution, natifs"
  - "erreurs d'exécution, débogage"
  - "erreurs d'exécution, vérification des erreurs"
  - "runtime_checks (pragma)"
  - "pointeurs de pile"
  - "pointeurs de pile, altération"
  - "pile, altération du pointeur"
  - "variables (débogueur), intercepter les dépendances par rapport à des variables locales non initialisées"
  - "variables (débogueur), perte de données"
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment&#160;: utiliser les contr&#244;les natifs &#224; l&#39;ex&#233;cution
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En Visual C\+\+, vous pouvez utiliser des [runtime\_checks](/visual-cpp/preprocessor/runtime-checks) natifs pour dépister les erreurs d’exécution courantes, telles que :  
  
-   Un pointeur de pile détérioré.  
  
-   Des dépassements de tableaux locaux.  
  
-   Une pile détériorée.  
  
-   Des dépendances avec des variables locales non initialisées.  
  
-   Une perte de données par suite d'une assignation à une variable plus courte.  
  
 Si vous utilisez **\/RTC** dans une version optimisée \(**\/O**\), il en résulte une erreur du compilateur. Un pragma `runtime_checks` n'a aucun effet s'il est utilisé dans une version optimisée.  
  
 Si les contrôles à l'exécution sont activés dans le programme que vous déboguez, par défaut, le programme s'arrête et entre dans le débogueur en cas d'erreur. Vous pouvez modifier ce comportement par défaut pour tout contrôle d'exécution. Pour plus d'informations, consultez [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Les procédures suivantes décrivent comment activer des contrôles d'exécution natifs dans une génération Debug et comment modifier le comportement du contrôle d'exécution natif.  
  
 Les autres rubriques de cette section fournissent des informations sur :  
  
-   [Personnalisation des contrôles d'exécution avec la bibliothèque Runtime C](../debugger/native-run-time-checks-customization.md)  
  
-   [Utilisation de contrôles d'exécution sans la bibliothèque Runtime C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### Pour activer les contrôles natifs à l'exécution dans une version Debug  
  
-   Utilisez l'option **\/RTC** et établissez une liaison avec la version Debug d'une bibliothèque Runtime C \(\/MDd, par exemple\).  
  
### Pour modifier le comportement du contrôle natif à l'exécution  
  
-   Utilisez le pragma `runtime_checks`.  
  
## Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [Vérifications des erreurs au moment de l'exécution](/visual-cpp/c-runtime-library/run-time-error-checking)
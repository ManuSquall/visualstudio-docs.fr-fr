---
title: "D&#233;bogage des applications en mode mixte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Pile des appels (fenêtre)"
  - "Pile des appels (fenêtre), débogage en mode mixte"
  - "déboguer (Visual Studio), mode mixte"
  - "déboguer le code managé, code mixte"
  - "débogage en mode mixte"
  - "débogage en mode mixte, pile des appels"
  - "débogage en mode mixte, évaluation de propriété"
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# D&#233;bogage des applications en mode mixte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une application en mode mixte est une application qui combine du code natif \(C\+\+\) avec du code managé \(tel que Visual Basic, Visual C\# ou C\+\+ qui s'exécute sur le Common Language Runtime\).  Le débogage d'applications en mode mixte est largement transparent dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il n'est pas très différent du débogage d'une application en mode unique.  Quelques considérations spéciales sont toutefois à prendre en compte.  
  
## Permettre l'opération Modifier & Continuer pour C\+\+ dans le cadre du débogage en mode mixte  
  
-   Pour pouvoir utiliser l'opération Modifier & Continuer pour C\+\+ dans Visual Studio 2013, vous devez revenir au moteur de débogage hérité.  Consultez [Basculement en mode de compatibilité managé dans Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) dans le blog relatif à la gestion du cycle de vie des applications Microsoft.  
  
## Évaluation de propriété dans les applications en mode mixte  
 Dans une application en mode mixte, l'évaluation des propriétés par le débogueur est une opération coûteuse.  Par conséquent, le débogage d'opérations telles que l'exécution pas à pas peut sembler lent.  Pour plus d'informations, consultez [Exécution pas à pas](http://msdn.microsoft.com/fr-fr/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  Si vos performances sont faibles lors du débogage en mode mixte, vous pouvez désactiver l'évaluation de propriété dans les fenêtres du débogueur.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### Pour désactiver l'évaluation de propriété  
  
1.  Dans le menu **Outils**, choisissez **Options**.  
  
2.  Dans la boîte de dialogue **Options**, ouvrez le dossier **Débogage** et sélectionnez la catégorie **Général**.  
  
3.  Désactivez la case à cocher **Activer l'évaluation de la propriété et d'autres appels de fonction implicite**.  
  
 Dans la mesure où les piles des appels natives et managées sont différentes, le débogueur ne peut pas toujours fournir la pile des appels complète pour le code mixte.  Lorsque le code natif appelle le code managé, il est possible que vous notiez certaines divergences.  Pour plus d'informations, consultez [Code mixte et informations manquantes dans la fenêtre Pile des appels](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)
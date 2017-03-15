---
title: "Comment&#160;: appliquer des modifications en mode arr&#234;t &#224; l&#39;aide de la fonctionnalit&#233; Modifier &amp; Continuer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "mode arrêt, appliquer les modifications du code"
  - "code, modifier en mode arrêt"
  - "coder, modifier en mode arrêt"
  - "Modifier & Continuer (Visual Basic), appliquer des modifications en mode arrêt"
  - "Modifier & Continuer, appliquer des modifications en mode arrêt"
  - "modifier, mode arrêt"
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# Comment&#160;: appliquer des modifications en mode arr&#234;t &#224; l&#39;aide de la fonctionnalit&#233; Modifier &amp; Continuer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser Modifier & Continuer pour modifier votre code en mode Arrêt, puis continuer sans arrêter et redémarrer l'exécution.  
  
 Modifier & Continuer n'est pas disponible dans les scénarios de débogage suivants :  
  
-   Débogage en mode mixte \(natif\/managé\).  
  
-   Débogage SQL.  
  
-   Débogage d'un dump  Dr. Watson.  
  
-   Modification de code après une exception non gérée, lorsque l'option **Dérouler la pile des appels sur les exceptions non gérées** n'est pas sélectionnée.  
  
-   Débogage d'une application runtime incorporée.  
  
-   Débogage d'une application à l'aide de la commande **Attacher à** au lieu d'exécuter l'application en cliquant sur **Démarrer** dans le menu **Déboguer**.  
  
-   Débogage de code optimisé.  
  
-   Débogage de code managé lorsque la cible est une application 64 bits.  Pour utiliser Modifier & Continuer, vous devez affecter x86 à la cible.  \(**Propriétés** de *Project*, onglet **Compiler**, **Paramètres avancés du compilateur**.\).  
  
-   Débogage d'une version ancienne de votre code après un échec de génération par une nouvelle version en raison d'erreurs de build.  
  
### Pour modifier du code en mode Arrêt  
  
1.  Passez en mode Arrêt en procédant de l'une des manières suivantes :  
  
    -   Définissez un point d'arrêt dans votre code, puis cliquez sur **Démarrer le débogage** dans le menu **Déboguer** et attendez que l'application parvienne au point d'arrêt.  
  
         – ou –  
  
    -   Démarrez le débogage, puis sélectionnez **Interrompre tout** dans le menu **Déboguer**.  
  
         – ou –  
  
    -   Lorsqu'une exception se produit, cliquez sur **Activer la modification** dans l'**Assistant Exception**.  
  
2.  Apportez toutes les modifications de code souhaitées et autorisées.  
  
     Pour plus d'informations, consultez [Modifications non prises en charge dans Modifier & Continuer \(Visual Basic\)](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Si vous tentez d'effectuer une modification du code qui n'est pas autorisée par l'opération Modifier & Continuer, votre modification est soulignée d'un trait ondulé violet et une tâche s'affiche dans la liste des tâches.  Il vous est impossible de continuer l'exécution du code sauf si vous annulez la modification de code non autorisée.  
  
3.  Dans le menu **Déboguer**, cliquez sur **Continuer** pour reprendre l'exécution.  
  
     Votre code s'exécute désormais avec les modifications que vous avez appliquées dans le projet.  
  
## Voir aussi  
 [Modifications non prises en charge dans Modifier & Continuer \(Visual Basic\)](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Modifier & Continuer \(Visual Basic\)](../debugger/edit-and-continue-visual-basic.md)
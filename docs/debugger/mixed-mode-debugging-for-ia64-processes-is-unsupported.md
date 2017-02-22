---
title: "Le d&#233;bogage en mode mixte des processus IA64 n&#39;est pas pris en charge. | Microsoft Docs"
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
  - "vs.debug.error.interop_unsupported_ia64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Le d&#233;bogage en mode mixte des processus IA64 n&#39;est pas pris en charge.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio ne prend pas en charge le débogage en mode mixte du code natif et managé dans les processus IA64.  Autrement dit, vous ne pouvez pas passer du code managé au code natif, ou inversement, lorsque vous procédez au débogage.  
  
### Solutions  
  
-   Déboguez votre code managé et natif dans des sessions de débogage distinctes.  
  
     \- ou \-  
  
     Déboguez votre code mixte en tant que processus 32 bits, de la façon décrite dans les procédures suivantes.  
  
### Pour passer en plateforme 32 bits \(Visual Basic ou C\#\)  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **Propriétés** dans le menu contextuel.  
  
2.  Dans les pages de propriétés, cliquez sur l'onglet **Compiler** ou **Déboguer**.  
  
3.  Cliquez sur **Plateforme** et sélectionnez x86 dans la liste.  
  
     Par défaut, les compilateurs C\# et Visual Basic génèrent du code à exécuter sur n'importe quelle UC.  Sur un ordinateur 64 bits, ces fichiers binaires sont exécutés en tant que processus 64 bits.  Pour une exécution sur un processus 32 bits, vous devez sélectionner **Win32**, et non **AnyCPU**.  
  
### Pour passer en plateforme 32 bits \(C\/C\+\+\)  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **Propriétés** dans le menu contextuel.  
  
2.  Dans les pages de propriétés, cliquez sur **Plateforme**, puis sélectionnez Win32 dans la liste.  
  
## Voir aussi  
 [Déboguer des applications 64 bits](../debugger/debug-64-bit-applications.md)
---
title: "Le d&#233;bogage en mode mixte est uniquement pris en charge lorsque vous utilisez Microsoft .NET Framework&#160;2.0 ou&#160;3.0 | Microsoft Docs"
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
  - "vs.debug.error.interop_unsupported_to_old"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Le d&#233;bogage en mode mixte est uniquement pris en charge lorsque vous utilisez Microsoft .NET Framework&#160;2.0 ou&#160;3.0
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les versions de Microsoft .NET Framework antérieures à la version 2.0 ne prennent pas en charge le débogage en mode mixte de processus 64 bits.  Cela signifie que vous ne pouvez pas passer du code managé au code natif, ou inversement, lorsque vous procédez au débogage.  
  
 Pour éviter ce problème, vous pouvez :  
  
-   mettre à jour votre projet pour utiliser Microsoft .NET Framework 2.0 ou 3.0 ;  
  
-   déboguer votre code managé et natif lors de différentes sessions de débogage ;  
  
-   déboguer votre code mixte en tant que processus 32 bits, comme décrit dans les procédures suivantes.  
  
### Pour faire passer le système d'exploitation à 32 bits \(Visual Basic ou C\#\)  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **Propriétés** dans le menu contextuel.  
  
2.  Dans les pages de propriétés, cliquez sur l'onglet **Compiler** ou **Déboguer**.  
  
3.  Cliquez sur **Plateforme**, puis sélectionnez **x86** dans la liste de plateformes.  
  
     Par défaut, les compilateurs C\# et Visual Basic génèrent le code à exécuter sur n'importe quelle UC.  Sur un ordinateur 64 bits, ces binaires sont exécutés en tant que processus 64 bits.  Pour une exécution sur un processus 32 bits, vous devez sélectionner **Win32**, et non **AnyCPU**.  
  
### Pour faire passer le système d'exploitation à 32 bits \(C\/C\+\+\)  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **Propriétés** dans le menu contextuel.  
  
     Dans les pages de propriétés, cliquez sur **Plateforme**, puis sélectionnez **Win32** dans la liste de plateformes.  
  
### Pour corriger cette erreur  
  
-   Consultez [Setting Up SQL Debugging](http://msdn.microsoft.com/fr-fr/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## Voir aussi  
 [Déboguer des applications 64 bits](../debugger/debug-64-bit-applications.md)
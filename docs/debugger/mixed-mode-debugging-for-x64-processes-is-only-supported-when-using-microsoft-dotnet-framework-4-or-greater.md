---
title: "Le d&#233;bogage en mode mixte des processus x64 est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework&#160;4 ou version ult&#233;rieure | Microsoft Docs"
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
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Le d&#233;bogage en mode mixte des processus x64 est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework&#160;4 ou version ult&#233;rieure
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les versions du .NET Framework antérieures à la version 4 ne prennent pas en charge le débogage en mode mixte des processus x64.  Cela signifie que vous ne pouvez pas passer du code managé au code natif, ou inversement, lorsque vous procédez au débogage.  
  
### Solutions  
  
-   Mettez votre projet à jour de façon à utiliser Microsoft .NET Framework 4 ou version ultérieure.  
  
     \- ou \-  
  
     Déboguez votre code managé et natif dans des sessions de débogage distinctes.  
  
     \- ou \-  
  
     Déboguez votre code mixte en tant que processus 32 bits, de la façon décrite dans les procédures suivantes.  
  
### Pour passer en plateforme 32 bits \(Visual Basic ou C\#\)  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.  
  
2.  Dans les pages de propriétés, cliquez sur l'onglet **Compiler** ou **Déboguer**.  
  
3.  Cliquez sur **Plateforme** et sélectionnez x86 dans la liste.  
  
     Par défaut, les compilateurs C\# et Visual Basic génèrent du code à exécuter sur n'importe quelle UC.  Sur un ordinateur 64 bits, ces fichiers binaires sont exécutés en tant que processus 64 bits.  Pour une exécution sur un processus 32 bits, vous devez sélectionner **Win32**, et non **AnyCPU**.  
  
### Pour passer en plateforme 32 bits \(C\/C\+\+\)  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Propriétés**.  
  
2.  Dans les pages de propriétés, cliquez sur **Plateforme**, puis sélectionnez Win32 dans la liste.  
  
### Pour corriger cette erreur  
  
-   Consultez [Setting Up SQL Debugging](http://msdn.microsoft.com/fr-fr/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## Voir aussi  
 [Déboguer des applications 64 bits](../debugger/debug-64-bit-applications.md)
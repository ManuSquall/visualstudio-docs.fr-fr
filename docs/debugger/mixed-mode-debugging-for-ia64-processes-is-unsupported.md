---
title: Le débogage en mode mixte des processus IA64 n'est pas pris en charge. | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab73d41442b97ed00045ba794a04bb2d23bb78cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Le débogage en mode mixte des processus IA64 n'est pas pris en charge.
Visual Studio ne prend pas en charge le débogage en mode mixte du code natif et managé dans les processus IA64. Autrement dit, vous ne pouvez pas passer du code managé au code natif, ou inversement, lorsque vous procédez au débogage.  
  
### <a name="workarounds"></a>Solutions  
  
-   Déboguez votre code managé et natif dans des sessions de débogage distinctes.  
  
     - ou -  
  
     Déboguez votre code mixte en tant que processus 32 bits, de la façon décrite dans les procédures suivantes.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Pour passer en plateforme 32 bits (Visual Basic ou C#)  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit sur votre projet, puis cliquez sur **propriétés** dans le menu contextuel.  
  
2.  Dans les pages de propriétés, cliquez sur le **compiler** ou **déboguer** onglet.  
  
3.  Cliquez sur **plateforme** et sélectionnez x86 dans la liste des plateformes.  
  
     Par défaut, les compilateurs C# et Visual Basic génèrent du code à exécuter sur n'importe quelle UC. Sur un ordinateur 64 bits, ces fichiers binaires sont exécutés en tant que processus 64 bits. Pour exécuter un processus 32 bits, vous devez choisir **Win32**, et non **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Pour passer en plateforme 32 bits (C/C++)  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit sur votre projet, puis cliquez sur **propriétés** dans le menu contextuel.  
  
2.  Dans les Pages de propriétés, cliquez sur **plateforme** puis sélectionnez Win32 dans la liste des plates-formes,  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer des applications 64 bits](../debugger/debug-64-bit-applications.md)
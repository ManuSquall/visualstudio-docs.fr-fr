---
title: "Débogage en Mode mixte est uniquement pris en charge lors de l’utilisation de Microsoft .NET Framework 2.0 ou 3.0 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd022d8f0a0e38ffbd7402c69f622df74e24bc30
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Le débogage en mode mixte est uniquement pris en charge lorsque vous utilisez Microsoft .NET Framework 2.0 ou 3.0
Les versions de Microsoft .NET Framework antérieures à la version 2.0 ne prennent pas en charge le débogage en mode mixte de processus 64 bits. Cela signifie que vous ne pouvez pas passer du code managé au code natif, ou inversement, lorsque vous procédez au débogage.  
  
 Pour éviter ce problème, vous pouvez :  
  
-   mettre à jour votre projet pour utiliser Microsoft .NET Framework 2.0 ou 3.0 ;  
  
-   Déboguez votre code managé et natif dans des sessions de débogage distinctes.  
  
-   Déboguez votre code mixte en tant que processus 32 bits, de la façon décrite dans les procédures suivantes.  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Pour faire passer le système d'exploitation à 32 bits (Visual Basic ou C#)  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit de votre projet, puis cliquez sur **propriétés** dans le menu contextuel.  
  
2.  Dans les pages de propriétés, cliquez sur le **compiler** ou **déboguer** onglet.  
  
3.  Cliquez sur **plateforme**, puis sélectionnez **x86** dans la liste des plateformes.  
  
     Par défaut, les compilateurs C# et Visual Basic génèrent le code à exécuter sur n'importe quelle UC. Sur un ordinateur 64 bits, ces fichiers binaires sont exécutés en tant que processus 64 bits. Pour exécuter un processus 32 bits, vous devez choisir **Win32**, et non **AnyCPU**.  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Pour faire passer le système d'exploitation à 32 bits (C/C++)  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit de votre projet, puis cliquez sur **propriétés** dans le menu contextuel.  
  
     Dans les pages de propriétés, cliquez sur **plateforme**, puis sélectionnez **Win32** dans la liste des plateformes.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Consultez [configurer le débogage SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer des applications 64 bits](../debugger/debug-64-bit-applications.md)
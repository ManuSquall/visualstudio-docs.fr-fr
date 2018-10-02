---
title: En mode mixte débogage pour x64 processus est uniquement pris en charge lors de l’utilisation de Microsoft.NET Framework 4 ou supérieur | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0297d9bcfb380261d2ad2e73853ded70285f1b35
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495955"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Le débogage en mode mixte des processus x64 est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework 4 ou version ultérieure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [mixte de débogage pour x64 processus est uniquement pris en charge lors de l’utilisation de Microsoft.NET Framework 4 ou supérieur](https://docs.microsoft.com/visualstudio/debugger/mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoft-dotnet-framework-4-or-greater).  
  
NET Framework versions antérieures à 4 ne fournissent pas prise en charge pour le débogage en mode mixte de x64 traite. Cela signifie que vous ne pouvez pas passer du code managé au code natif, ou inversement, lorsque vous procédez au débogage.  
  
### <a name="workarounds"></a>Solutions  
  
-   Mettez votre projet à jour de façon à utiliser Microsoft .NET Framework 4 ou version ultérieure.  
  
     – ou –  
  
     Déboguez votre code managé et natif dans des sessions de débogage distinctes.  
  
     – ou –  
  
     Déboguez votre code mixte en tant que processus 32 bits, de la façon décrite dans les procédures suivantes.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Pour passer en plateforme 32 bits (Visual Basic ou C#)  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur votre projet, puis cliquez sur **propriétés**.  
  
2.  Dans les pages de propriétés, cliquez sur le **compiler** ou **déboguer** onglet.  
  
3.  Cliquez sur **plateforme** et sélectionnez x86 dans la liste des plateformes.  
  
     Par défaut, les compilateurs C# et Visual Basic génèrent du code à exécuter sur n'importe quelle UC. Sur un ordinateur 64 bits, ces fichiers binaires sont exécutés en tant que processus 64 bits. Pour exécuter un processus 32 bits, vous devez choisir **Win32**, et non **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Pour passer en plateforme 32 bits (C/C++)  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur votre projet, puis cliquez sur **propriétés**.  
  
2.  Dans les Pages de propriétés, cliquez sur **plateforme** puis sélectionnez Win32 dans la liste des plateformes.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Consultez [configuration du débogage SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer des applications 64 bits](../debugger/debug-64-bit-applications.md)




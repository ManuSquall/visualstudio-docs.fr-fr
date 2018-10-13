---
title: 'Erreur : Mixte en mode débogage pour x64 processus est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework 4 ou supérieur | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82440d378e34c5808e9bcb250172f6c1abfbfdf6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239237"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erreur : Le débogage en mode mixte des processus x64 est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework 4 ou version ultérieure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour déboguer du code natif et managé mixte dans un processus 64 bits, vous devez disposer du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] version 4. Le débogage en mode mixte de processus 64 bits avec les versions de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] antérieures à la version 4 n'est pas pris en charge.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Effectuez l’une des opérations suivantes :  
  
    -   Effectuez une mise à niveau du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] vers la version 4.  
  
    -   Générez une version 32 bits de votre application pour le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les outils de contrôle à distance sur le périphérique](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)




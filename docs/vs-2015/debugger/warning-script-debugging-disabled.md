---
title: 'Avertissement : Script de débogage est désactivé | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b44c260e00ae5ef8b0d23e7aede139563ff22d98
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950750"
---
# <a name="warning-script-debugging-disabled"></a>Avertissement : le débogage de script est désactivé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogage de script est actuellement désactivé dans Internet Explorer  
  
 Ce message d'avertissement s'affiche lorsque vous essayez de déboguer le script sans activer le débogage de script dans Internet Explorer. Pour des raisons de sécurité, Internet Explorer désactive le débogage de script par défaut.  
  
### <a name="to-enable-script-debugging-in-internet-explorer"></a>Pour activer le débogage de script dans Internet Explorer  
  
1.  Dans le menu **Outils** d’Internet Explorer, sélectionnez **Options Internet**.  
  
2.  Dans la boîte de dialogue **Options Internet** , cliquez sur l’onglet **Avancé** .  
  
3.  Sous l’onglet **Avancé**, consultez la zone **Paramètres**, catégorie **Navigation**.  
  
4.  Désactivez la case à cocher **Désactiver le débogage des scripts (Internet Explorer)**.  
  
5.  Cliquez sur **OK**.  
  
6.  Quittez, puis redémarrez Internet Explorer.  
  
     Les nouveaux paramètres sont désormais appliqués.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour attacher à un script](../debugger/how-to-attach-to-script.md)

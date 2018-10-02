---
title: 'Avertissement : Script est désactivé débogage | Microsoft Docs'
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
- vs.debug.scriptdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91b54b3e9a70284dc1efb03be7adfaa5d1421920
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495483"
---
# <a name="warning-script-debugging-disabled"></a>Avertissement : le débogage de script est désactivé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Avertissement : le débogage de Script est désactivé](https://docs.microsoft.com/visualstudio/debugger/warning-script-debugging-disabled).  
  
Le débogage de script est actuellement désactivé dans Internet Explorer  
  
 Ce message d'avertissement s'affiche lorsque vous essayez de déboguer le script sans activer le débogage de script dans Internet Explorer. Pour des raisons de sécurité, Internet Explorer désactive le débogage de script par défaut.  
  
### <a name="to-enable-script-debugging-in-internet-explorer"></a>Pour activer le débogage de script dans Internet Explorer  
  
1.  Dans Internet Explorer **outils** menu, choisissez **Options Internet**.  
  
2.  Dans la boîte de dialogue **Options Internet** , cliquez sur l’onglet **Avancé** .  
  
3.  Sur le **avancé** onglet, consultez le **paramètres** boîte, **navigation** catégorie.  
  
4.  Effacer **désactiver le débogage des scripts (Internet Explorer)**.  
  
5.  Cliquez sur **OK**.  
  
6.  Quittez, puis redémarrez Internet Explorer.  
  
     Les nouveaux paramètres sont désormais appliqués.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour attacher à un script](../debugger/how-to-attach-to-script.md)




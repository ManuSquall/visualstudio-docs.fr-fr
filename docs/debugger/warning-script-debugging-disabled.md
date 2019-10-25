---
title: 'AVERTISSEMENT : débogage de script désactivé | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91875a370f6d072cf2dd69807f516b8f1a808461
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728198"
---
# <a name="warning-script-debugging-disabled"></a>Avertissement : le débogage de script est désactivé
Le débogage de script est actuellement désactivé dans Internet Explorer

 Ce message d'avertissement s'affiche lorsque vous essayez de déboguer le script sans activer le débogage de script dans Internet Explorer. Pour des raisons de sécurité, Internet Explorer désactive le débogage de script par défaut.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Pour activer le débogage de script dans Internet Explorer

1. Dans le menu **Outils** d’Internet Explorer, sélectionnez **Options Internet**.

2. Dans la boîte de dialogue **Options Internet** , cliquez sur l’onglet **Avancé** .

3. Sous l’onglet **Avancé**, consultez la zone **Paramètres**, catégorie **Navigation**.

4. Désactivez la case à cocher **Désactiver le débogage des scripts (Internet Explorer)** .

5. Cliquez sur **OK**.

6. Quittez, puis redémarrez Internet Explorer.

     Les nouveaux paramètres sont désormais appliqués.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour attacher à un script](../debugger/how-to-attach-to-script.md)
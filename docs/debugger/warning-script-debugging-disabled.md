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
ms.openlocfilehash: 15de1a1e516cb3d84c24428ef04dd87baedaed9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81648501"
---
# <a name="warning-script-debugging-disabled"></a>Avertissement : le débogage de script est désactivé
Le débogage de script est actuellement désactivé dans Internet Explorer

 Ce message d'avertissement s'affiche lorsque vous essayez de déboguer le script sans activer le débogage de script dans Internet Explorer. Pour des raisons de sécurité, Internet Explorer désactive le débogage de script par défaut.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Pour activer le débogage de script dans Internet Explorer

1. Dans le menu **Outils** d’Internet Explorer, sélectionnez **Options Internet**.

2. Dans la boîte de dialogue **Options Internet** , cliquez sur l’onglet **Avancé** .

3. Sous l’onglet **Avancé**, consultez la zone **Paramètres**, catégorie **Navigation**.

4. Désactivez la case à cocher **Désactiver le débogage des scripts (Internet Explorer)**.

5. Cliquez sur **OK**.

6. Quittez, puis redémarrez Internet Explorer.

     Les nouveaux paramètres sont désormais appliqués.

## <a name="see-also"></a>Voir aussi
- [Comment : attacher à un script](attach-to-running-processes-with-the-visual-studio-debugger.md)
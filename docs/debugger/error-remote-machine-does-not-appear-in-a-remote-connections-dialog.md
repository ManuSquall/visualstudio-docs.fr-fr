---
title: L’ordinateur distant n’apparaît pas dans une boîte de dialogue connexions à distance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5392a6219b1bf8bf42146cacf8216a63f1fa3832
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852561"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Erreur : l’ordinateur distant n’apparaît pas dans une boîte de dialogue Connexions à distance
Si l’ordinateur distant n’apparaît pas dans la boîte de dialogue Connexions à distance, vérifiez les causes courantes suivantes.

 Si vous utilisez le mode de compatibilité managé, consultez la documentation de Visual Studio 2010 : [Dépannage du débogage distant - Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Causes courantes de cette erreur

- L’ordinateur distant s’exécute sur un ordinateur qui se trouve dans un sous-réseau différent. Pour résoudre ce problème, tapez manuellement le nom ou l’adresse IP de l’ordinateur dans la boîte de dialogue Qualificateur

- Le débogueur distant ne fonctionne pas sur l’ordinateur distant. Pour résoudre ce problème, démarrez le débogueur distant.

- Le pare-feu bloque les communications entre Visual Studio et l’ordinateur distant. Pour résoudre ce problème, configurez votre pare-feu pour permettre à Visual Studio et au débogueur distant (msvsmon) de communiquer.

- Un logiciel antivirus bloque les communications entre Visual Studio et l’ordinateur distant. Pour résoudre ce problème, configurez le logiciel antivirus pour permettre à Visual Studio et au débogueur distant (msvsmon) de communiquer.

## <a name="see-also"></a>Voir aussi
- [Débogage à distance](../debugger/remote-debugging.md)
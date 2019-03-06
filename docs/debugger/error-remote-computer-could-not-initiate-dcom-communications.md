---
title: 'Erreur : Ordinateur distant Impossible d’initialiser les communications DCOM | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
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
ms.openlocfilehash: 9e936292010c73decffadc5b215156f2200ed8b3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683072"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Erreur : L'ordinateur distant n'a pas pu initier les communications DCOM
Une erreur DCOM s'est produite lorsque l'ordinateur distant a tenté de communiquer avec l'ordinateur local. L'ordinateur local est l'ordinateur qui

 exécute Visual Studio. Cette erreur peut se produire pour plusieurs raisons :

-   L'ordinateur local a un pare-feu activé.

-   L'authentification Windows de l'ordinateur distant vers l'ordinateur local ne fonctionne pas.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1.  Si l’ordinateur local a un pare-feu Windows est activé, consultez [le débogage à distance](../debugger/remote-debugging.md) pour obtenir des instructions sur la façon de configurer le pare-feu pour le débogage local.

2.  Testez l'authentification Windows en essayant d'ouvrir un partage de fichiers sur l'ordinateur local du serveur distant.

3.  Pour restaurer l'authentification Windows, tentez de redémarrer les deux ordinateurs. Vérifiez si les journaux des événements de l'ordinateur local ou distant contiennent des erreurs Kerberos et contactez les administrateurs de domaines pour les problèmes connus.

## <a name="see-also"></a>Voir aussi
 [Remote Debugging](../debugger/remote-debugging.md)
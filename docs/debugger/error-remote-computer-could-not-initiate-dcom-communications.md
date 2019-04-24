---
title: 'Erreur : Ordinateur distant n’a pas pu lancer les communications DCOM | Microsoft Docs'
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
ms.openlocfilehash: 7ceb796b3a4b3cbc2b239a09ac8c173e746f194c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091198"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Erreur : L’ordinateur distant n’a pas pu lancer les communications DCOM
Une erreur DCOM s'est produite lorsque l'ordinateur distant a tenté de communiquer avec l'ordinateur local. L'ordinateur local est l'ordinateur qui

 exécute Visual Studio. Cette erreur peut se produire pour plusieurs raisons :

- L'ordinateur local a un pare-feu activé.

- L'authentification Windows de l'ordinateur distant vers l'ordinateur local ne fonctionne pas.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Si l’ordinateur local a un pare-feu Windows est activé, consultez [le débogage à distance](../debugger/remote-debugging.md) pour obtenir des instructions sur la façon de configurer le pare-feu pour le débogage local.

2. Testez l'authentification Windows en essayant d'ouvrir un partage de fichiers sur l'ordinateur local du serveur distant.

3. Pour restaurer l'authentification Windows, tentez de redémarrer les deux ordinateurs. Vérifiez si les journaux des événements de l'ordinateur local ou distant contiennent des erreurs Kerberos et contactez les administrateurs de domaines pour les problèmes connus.

## <a name="see-also"></a>Voir aussi
 [Remote Debugging](../debugger/remote-debugging.md)
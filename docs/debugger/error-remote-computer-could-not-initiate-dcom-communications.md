---
description: Une erreur DCOM s'est produite lorsque l'ordinateur distant a tenté de communiquer avec l'ordinateur local.
title: L’ordinateur distant n’a pas pu initialiser les communications DCOM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 86d6c46f338d789d6b113551ac9d99c681290526
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146780"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Erreur : L'ordinateur distant n'a pas pu initier les communications DCOM
Une erreur DCOM s'est produite lorsque l'ordinateur distant a tenté de communiquer avec l'ordinateur local. L'ordinateur local est l'ordinateur qui

 exécute Visual Studio. Cette erreur peut se produire pour plusieurs raisons :

- L'ordinateur local a un pare-feu activé.

- L'authentification Windows de l'ordinateur distant vers l'ordinateur local ne fonctionne pas.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Si le pare-feu Windows est activé sur l’ordinateur local, consultez [débogage distant](../debugger/remote-debugging.md) pour obtenir des instructions sur la configuration du pare-feu pour le débogage local.

2. Testez l'authentification Windows en essayant d'ouvrir un partage de fichiers sur l'ordinateur local du serveur distant.

3. Pour restaurer l'authentification Windows, tentez de redémarrer les deux ordinateurs. Vérifiez si les journaux des événements de l'ordinateur local ou distant contiennent des erreurs Kerberos et contactez les administrateurs de domaines pour les problèmes connus.

## <a name="see-also"></a>Voir aussi
 [Débogage à distance](../debugger/remote-debugging.md)

---
title: "Erreur : Microsoft Visual Studio Remote Debugging Monitor sur l'ordinateur distant ne dispose pas des autorisations pour se connecter à cet ordinateur"
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac6e632927878988f8a3ff86d63fea080a45bd6d
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55852986"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Erreur : Microsoft Visual Studio Remote Debugging Monitor sur l'ordinateur distant ne dispose pas des autorisations pour se connecter à cet ordinateur

Cette erreur ce produit lorsque l'utilisateur qui tente d'exécuter Visual Studio Remote Debugging Monitor (msvsmon) ne possède pas de compte sur l'ordinateur local.

## <a name="to-fix-this-problem"></a>Pour corriger ce problème

- Ajoutez un compte d'utilisateur à l'ordinateur hôte du débogueur Visual Studio, en utilisant les mêmes nom et mot de passe que le compte d'utilisateur qui exécute msvsmon sur l'ordinateur distant.

   \- ou -

- Exécutez msvsmon en tant qu'utilisateur autorisé à appeler l'ordinateur local. Cela signifie que l'utilisateur doit être un utilisateur de domaine et un administrateur sur l'ordinateur msvsmon. Vous pouvez spécifier le compte d'utilisateur qui doit exécuter msvsmon de deux manières différentes :

  - Cliquez avec le bouton droit sur l’icône msvsmon et choisissez **Exécuter en tant que** dans le menu contextuel

    \- ou -

  - À l'invite de commandes, tapez `runas.exe`.

## <a name="see-also"></a>Voir aussi

- [Erreurs et résolution des problèmes du débogage distant](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
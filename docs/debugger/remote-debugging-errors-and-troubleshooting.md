---
title: Erreurs de débogage à distance et dépannage Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b413ce193e6761d515de5bc5ef30fae8e18a3a3
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302090"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Erreurs de débogage distant et dépannage

Vous pouvez rencontrer les erreurs suivantes lorsque vous tentez de déboiffer à distance.

- [Erreur: Impossible d’entrer automatiquement dans le serveur](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Erreur : Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) ne semble pas s’exécuter sur l’ordinateur distant](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Impossible de se connecter au Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Erreur : l’ordinateur distant n’apparaît pas dans une boîte de dialogue Connexions à distance](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Exécuter le débbugger à distance en tant qu’administrateur

Vous pouvez rencontrer des problèmes si vous n’exécutez pas le débbugger à distance en tant qu’administrateur. Par exemple, vous pouvez voir l’erreur suivante : « Le Visual Studio Remote Debugger (MSVSMON. EXE) n’a pas les privilèges suffisants pour déboquer ce processus. Si vous exécutez le débbugger à distance comme une application (pas un service), vous pouvez voir l’erreur [de compte utilisateur différent.](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)

### <a name="when-running-the-remote-debugger-as-a-service"></a>Lors de l’exécution du débbugger à distance comme un service

Lorsque nous exécutez le débbugger à distance comme service, nous vous recommandons de l’exécuter en tant qu’administrateur pour plusieurs raisons :

- Le service de débogé à distance ne permet que les connexions des administrateurs, de sorte qu’il **n’y a pas** de nouveaux risques de sécurité introduits en l’exécutant en tant qu’administrateur.

- Il peut prévenir les erreurs qui résultent lorsque l’utilisateur Visual Studio a plus de droits de débog d’un processus que le débbugger à distance lui-même ne.

- Pour simplifier la configuration et la configuration du débbuggeur à distance.

Bien qu’il soit possible de déboguer sans exécuter le débbugger à distance en tant qu’administrateur, il ya plusieurs exigences pour faire ce travail correctement et ils nécessitent souvent des étapes de configuration de service plus avancés.

- Le compte que vous utilisez sur la machine à distance doit avoir le logon comme privilège **de service.** Voir les étapes sous "Ajouter logon comme un service" dans l’article [d’erreur de retour ne peut pas se connecter.](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)

- Le compte doit avoir le droit de déboiffer le processus cible. Pour obtenir ces droits, vous devez exécuter le débbugger à distance sous le même compte que le processus à déboguer. (L’alternative la plus facile est d’exécuter le service en tant qu’administrateur.) 

- Le compte doit être en mesure de se connecter à (c’est-à-dire, authentifier avec) l’ordinateur Visual Studio sur le réseau. Sur un domaine, il est plus facile de se connecter en arrière si le débbuggeur à distance est en cours d’exécution sous les comptes intégrés de système local ou de service de réseau, ou un compte de domaine. Les comptes intégrés ont des privilèges de sécurité élevés qui peuvent présenter un risque pour la sécurité.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Lors de l’exécution du débbugger à distance comme une application (mode normal)

Si vous essayez de vous attacher à votre propre processus non élevé (comme une application normale), peu importe si vous exécutez le débbugger à distance en tant qu’administrateur.

Vous souhaitez exécuter le débbugger à distance en tant qu’administrateur dans plusieurs scénarios:

- Vous souhaitez vous attacher à des processus en cours d’exécution en tant qu’un autre utilisateur (comme lors de la débogage IIS), ou

- Vous essayez de lancer un autre processus, et le processus que vous souhaitez lancer est un administrateur.

Vous ne voulez **pas** vous exécuter en tant qu’administrateur si vous souhaitez lancer des processus, et le processus que vous souhaitez lancer ne doit **pas** être un administrateur.

## <a name="see-also"></a>Voir aussi
- [Débugging à distance](../debugger/remote-debugging.md)
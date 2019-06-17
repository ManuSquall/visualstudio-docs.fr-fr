---
title: Erreurs de débogage distant et dépannage | Microsoft Docs
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
ms.openlocfilehash: 078551111223f11b38f3192075caa9ddfabaf18c
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043347"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Erreurs de débogage distant et dépannage

Vous pouvez rencontrer les erreurs suivantes lorsque vous tentez de déboguer à distance.

- [Erreur : impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Erreur : Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) ne semble pas s’exécuter sur l’ordinateur distant.](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Erreur : l’ordinateur distant n’apparaît pas dans une boîte de dialogue Connexions à distance](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Exécuter le débogueur distant en tant qu’administrateur

Vous risquez de rencontrer des problèmes si vous n’exécutez le débogueur distant en tant qu’administrateur. Par exemple, vous pouvez voir l’erreur suivante : « Le débogueur distant Visual Studio (MSVSMON. (EXE) dispose de privilèges suffisants pour déboguer ce processus. » Si vous exécutez le débogueur distant en tant qu’application (pas un service), vous pouvez voir le [autre compte d’utilisateur](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) erreur.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Lors de l’exécution du débogueur distant en tant que service

Lorsque vous exécutez le débogueur distant en tant que service de s, nous vous recommandons d’exécuter en tant qu’administrateur pour plusieurs raisons :

- Le service débogueur distant autorise uniquement les connexions des administrateurs, il n’y **aucune** nouveaux risques de sécurité introduites en l’exécutant en tant qu’administrateur.

- Il peut empêcher les erreurs de résultat lorsque l’utilisateur de Visual Studio a davantage de droits pour déboguer un processus que le débogueur distant lui-même ne.

- Pour simplifier l’installation et la configuration du débogueur distant.

Bien qu’il soit possible de déboguer sans exécuter le débogueur distant en tant qu’administrateur, il existe plusieurs conditions requises pour que cela fonctionne correctement et qu’ils nécessitent souvent des étapes de configuration de service plus avancées.

- Le compte que vous utilisez sur l’ordinateur distant doit avoir le **ouverture de session en tant que service** privilège. Consultez les étapes décrites dans « Pour ajouter d’ouverture de session en tant que service » dans le [ne peut pas se connecter de nouveau](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) article de l’erreur.

- Le compte doit disposer des droits pour déboguer le processus cible. Pour obtenir ces droits, vous devez exécuter le débogueur distant sous le même compte que le processus à déboguer. (L’alternative plus simple consiste à exécuter le service en tant qu’administrateur.) 

- Le compte doit être en mesure de se connecter à la (autrement dit, s’authentifier avec) l’ordinateur Visual Studio sur le réseau. Sur un domaine, il est plus facile pour vous connecter si le débogueur distant s’exécute sous les comptes système Local ou Service réseau intégrés ou un compte de domaine. Les comptes intégrés ont des privilèges de sécurité qui peuvent présenter un risque de sécurité élevés.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Lors de l’exécution du débogueur distant en tant qu’application (mode normal)

Si vous tentez d’attacher à votre propre processus non élevés (par exemple, une application normale), peu importe si vous exécutez le débogueur distant en tant qu’administrateur.

Vous souhaitez exécuter le débogueur distant en tant qu’administrateur dans plusieurs scénarios :

- Vous souhaitez attacher aux processus en cours d’exécution en tant qu’un autre utilisateur (par exemple quand IIS de débogage), ou

- Vous tentez de lancer un autre processus, et le processus que vous souhaitez lancer est un administrateur.

Vous faire **pas** à exécuter en tant qu’administrateur si vous souhaitez lancer des processus et le processus que vous souhaitez lancer doit **pas** être un administrateur.

## <a name="see-also"></a>Voir aussi
- [Remote Debugging](../debugger/remote-debugging.md)
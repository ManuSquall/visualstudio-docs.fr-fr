---
title: Erreurs et résolution des problèmes de débogage à distance | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89316135"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Erreurs de débogage distant et dépannage

Vous pouvez rencontrer les erreurs suivantes lorsque vous tentez de déboguer à distance.

- [Erreur : impossible d’effectuer automatiquement un pas à pas détaillé sur le serveur](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Erreur : Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) ne semble pas s’exécuter sur l’ordinateur distant](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Impossible de se connecter à l'ordinateur Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Erreur : l’ordinateur distant n’apparaît pas dans une boîte de dialogue Connexions à distance](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Exécuter le débogueur distant en tant qu’administrateur

Vous risquez de rencontrer des problèmes si vous n’exécutez pas le débogueur distant en tant qu’administrateur. Par exemple, vous pouvez voir l’erreur suivante : « le Débogueur distant Visual Studio (MSVSMON.EXE) ne dispose pas des privilèges suffisants pour déboguer ce processus. » Si vous exécutez le débogueur distant en tant qu’application (pas un service), vous pouvez voir l’erreur de [compte d’utilisateur différente](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) .

### <a name="when-running-the-remote-debugger-as-a-service"></a>Lors de l’exécution du débogueur distant en tant que service

Lors de l’exécution du débogueur distant en tant que service s, nous vous recommandons de l’exécuter en tant qu’administrateur pour plusieurs raisons :

- Le service du débogueur distant autorise uniquement les connexions des administrateurs. il n’existe donc **aucun** nouveau risque de sécurité introduit par l’exécution en tant qu’administrateur.

- Cela peut empêcher des erreurs qui se produisent lorsque l’utilisateur Visual Studio dispose de plus de droits pour déboguer un processus que le débogueur distant lui-même.

- Pour simplifier l’installation et la configuration du débogueur distant.

Bien qu’il soit possible de déboguer sans exécuter le débogueur distant en tant qu’administrateur, il existe plusieurs conditions requises pour que cela fonctionne correctement et qu’elles nécessitent souvent des étapes de configuration de service plus avancées.

- Le compte que vous utilisez sur l’ordinateur distant doit disposer du privilège **ouvrir une session en tant que service** . Consultez les étapes de la section « pour ajouter une ouverture de session en tant que service » dans l’article [Impossible de se reconnecter](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) .

- Le compte doit disposer des droits pour déboguer le processus cible. Pour bénéficier de ces droits, vous devez exécuter le débogueur distant sous le même compte que le processus à déboguer. (L’alternative la plus simple consiste à exécuter le service en tant qu’administrateur.) 

- Le compte doit être en mesure de se reconnecter à (c’est-à-dire, s’authentifier avec) l’ordinateur Visual Studio sur le réseau. Sur un domaine, il est plus facile de se reconnecter si le débogueur distant s’exécute sous le système local intégré ou les comptes de service réseau, ou un compte de domaine. Les comptes intégrés ont des privilèges de sécurité élevés qui peuvent présenter un risque pour la sécurité.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Lors de l’exécution du débogueur distant en tant qu’application (mode normal)

Si vous essayez d’effectuer un attachement à votre propre processus non élevé (par exemple, une application normale), peu importe si vous exécutez le débogueur distant en tant qu’administrateur.

Vous souhaitez exécuter le débogueur distant en tant qu’administrateur dans plusieurs scénarios :

- Vous souhaitez attacher des processus qui s’exécutent en tant qu’un autre utilisateur (par exemple, lors du débogage d’IIS) ou

- Vous essayez de lancer un autre processus et le processus que vous souhaitez lancer est un administrateur.

Vous ne souhaitez **pas** exécuter en tant qu’administrateur si vous souhaitez lancer des processus et que le processus que vous souhaitez lancer **ne doit pas** être un administrateur.

## <a name="see-also"></a>Voir aussi
- [Débogage à distance](../debugger/remote-debugging.md)
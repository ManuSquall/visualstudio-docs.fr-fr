---
title: -Log (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0d2e6af25b4e0acc4aad88c33861e9d22a775b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846124"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Enregistre toute l'activité dans le fichier journal de résolution des problèmes. Ce fichier apparaît une fois que vous avez appelé `devenv /log` au moins une fois. Par défaut, le fichier journal est :

 *%APPDATA%* \Microsoft\VisualStudio\\*Version*\ActivityLog.xml

 où *Version* est la version de Visual Studio. Toutefois, vous pouvez spécifier un autre chemin d’accès et/ou nom de fichier.

## <a name="syntax"></a>Syntaxe

```cmd
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Notes
 Ce commutateur doit apparaître à la fin de la ligne de commande, après tous les autres commutateurs.

 Le journal est rédigé pour toutes les instances de Visual Studio que vous avez appelées avec le commutateur /log. Il ne consigne pas les instances de Visual Studio que vous avez appelées sans ce commutateur.

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
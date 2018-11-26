---
title: -ResetSettings (devenv.exe)
ms.date: 11/16/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 568a829ff10cbee535729361b7c95dd7db6814f5
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948061"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Restaure les paramètres par défaut de Visual Studio et lance automatiquement l’IDE Visual Studio. Réinitialise éventuellement les paramètres avec les valeurs d’un fichier *vssettings* spécifié.

Les paramètres par défaut sont déterminés par le profil sélectionné quand Visual Studio a été lancé pour la première fois.

> [!TIP]
> Pour savoir comment réinitialiser les paramètres à l’aide de l’environnement de développement intégré (IDE), consultez [Réinitialiser les paramètres](../synchronized-settings-in-visual-studio.md#reset-settings).

## <a name="syntax"></a>Syntaxe

```cmd
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Arguments

`SettingsFile`

Chemin complet et nom du fichier *.vssettings* à appliquer à Visual Studio.

Pour restaurer le profil des paramètres de développement généraux, utilisez `General`.

## <a name="remarks"></a>Notes

Si aucun `SettingsFile` n’est spécifié, vous êtes invité à sélectionner une collection de paramètres par défaut au prochain démarrage de Visual Studio.

## <a name="example"></a>Exemple

La ligne de commande suivante applique les paramètres stockés dans le fichier `MySettings.vssettings`.

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Voir aussi

- [Réinitialiser les paramètres](../synchronized-settings-in-visual-studio.md#reset-settings)
- [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
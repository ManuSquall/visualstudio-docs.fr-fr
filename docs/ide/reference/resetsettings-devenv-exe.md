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
ms.openlocfilehash: c8f826db0c619e1dfb5811aaf9d0c5ef40093c97
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388667"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Restaure les paramètres par défaut de Visual Studio et lance automatiquement l’IDE Visual Studio. Réinitialise éventuellement les paramètres avec les valeurs d’un fichier *vssettings* spécifié.

Les paramètres par défaut sont déterminés par le profil sélectionné quand Visual Studio a été lancé pour la première fois.

> [!TIP]
> Pour savoir comment réinitialiser les paramètres à l’aide de l’environnement de développement intégré (IDE), consultez [Réinitialiser les paramètres](../environment-settings.md#reset-settings).

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

- [Paramètres d’environnement](../environment-settings.md)
- [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
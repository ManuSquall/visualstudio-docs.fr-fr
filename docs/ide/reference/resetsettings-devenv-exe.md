---
title: -ResetSettings (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52c3576b10fdc88563b3689e4b37d71b7f4659cd
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227549"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Restaure les paramètres par défaut de Visual Studio et lance automatiquement l’IDE Visual Studio. Ce commutateur facultatif réinitialise les paramètres avec les valeurs d’un fichier de paramètres spécifié.

Les paramètres par défaut viennent du profil sélectionné quand Visual Studio a été lancé pour la première fois.

> [!TIP]
> Pour savoir comment réinitialiser les paramètres à l’aide de l’environnement de développement intégré (IDE), consultez [Réinitialiser les paramètres](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Syntaxe

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Arguments

- *SettingsFile*

  Optionnel. Chemin d’accès complet et nom du fichier de paramètres à appliquer à Visual Studio.

- *DefaultCollectionSpecifier*

  Optionnel. Spécificateur représentant une collection par défaut de paramètres à restaurer. Choisissez l’un des spécificateurs par défaut du tableau.

  | Nom de collection par défaut | Spécificateur de collection |
  | --- | --- |
  | **Général** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Développement web** | `Web` |
  | **Développement web (code uniquement)** | `WebCode` |

## <a name="remarks"></a>Notes

Si *SettingsFile* n’est pas spécifié, l’environnement IDE s’ouvre avec les paramètres existants.

## <a name="example"></a>Exemple

Le premier exemple applique les paramètres stockés dans le fichier `MySettings.vssettings`.

Le second exemple restaure le profil Visual C# par défaut.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Voir aussi

- [Paramètres d’environnement](../environment-settings.md)
- [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
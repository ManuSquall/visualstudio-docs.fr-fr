---
title: -Log (devenv.exe)
ms.date: 12/12/2018
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
ms.openlocfilehash: e6573bb8bb6118a38266c0b76ef435c59e6ccecb
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227237"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Enregistre toute l'activité dans le fichier journal de résolution des problèmes. Ce fichier apparaît une fois que vous avez appelé `devenv /log` au moins une fois. Par défaut, le fichier journal se trouve à l’emplacement :

**%APPDATA%\\Microsoft\\VisualStudio\\**\<Version\>**\\ActivityLog.xml**.

où \<Version\> est la version de Visual Studio. Toutefois, vous pouvez spécifier un autre chemin d’accès et/ou nom de fichier.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Arguments

- *NameOfLogFile*

  Obligatoire. Chemin d’accès complet et nom du fichier journal dans lequel sera effectué l’enregistrement.

## <a name="remarks"></a>Notes

Ce commutateur doit apparaître à la fin de la ligne de commande, après tous les autres commutateurs.

Le journal n’est consigné que pour les instances de Visual Studio ouvertes avec le commutateur `/Log`.

## <a name="example"></a>Exemple

Cet exemple dirige la journalisation vers le fichier `MyVSLog.xml` du répertoire de base de l’utilisateur.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
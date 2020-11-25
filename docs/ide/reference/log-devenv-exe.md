---
title: -Log (devenv.exe)
description: Découvrez comment utiliser le commutateur de ligne de commande log devenv pour enregistrer toutes les activités dans le fichier journal à des fins de dépannage.
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9dae594df60d75ced4ba6bdda5cb37c8c07a852
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040574"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Enregistre toute l'activité dans le fichier journal de résolution des problèmes. Ce fichier apparaît une fois que vous avez appelé `devenv /log` au moins une fois. Par défaut, le fichier journal se trouve à l’emplacement :

**% AppData% \\ActivityLog.xml\\ Microsoft \\ VisualStudio** \<Version\> **\\**

où \<Version\> est la version de Visual Studio. Toutefois, vous pouvez spécifier un autre chemin d'accès et/ou nom de fichier.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Arguments

- *NameOfLogFile*

  Obligatoire. Chemin d’accès complet et nom du fichier journal dans lequel sera effectué l’enregistrement.

## <a name="remarks"></a>Remarques

Ce commutateur doit apparaître à la fin de la ligne de commande, après tous les autres commutateurs.

Le journal n’est consigné que pour les instances de Visual Studio ouvertes avec le commutateur `/Log`.

## <a name="example"></a>Exemple

Cet exemple dirige la journalisation vers le fichier `MyVSLog.xml` du répertoire de base de l’utilisateur.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)

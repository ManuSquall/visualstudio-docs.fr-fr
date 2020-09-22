---
title: wsl-install
description: devinit outil WSL-install.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 1a52027c060917e8c5f692f472427ba5d980b3bb
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005056"
---
# <a name="wsl-install"></a>wsl-install

L' `wsl-install` outil permet d’installer Linux distributions pour le [sous-système Windows pour Linux](https://docs.microsoft.com/windows/wsl/) (WSL).

L' `wsl-install` outil requiert que WSL 2 soit déjà activé sur Windows. Si, pour une raison quelconque, WSL2 n’est pas activé, vous pouvez activer WSL2 à l’aide de l’outil [WindowsFeature-Enable](tool-windowsfeature-enable.md) et du nom de la fonctionnalité `Microsoft-Windows-Subsystem-Linux` .

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                             |
| [**entrée**](#input)                              | string | Oui      | Distribution à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.     |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.  |

### <a name="input"></a>Entrée

URI du package de distribution d’applications AppX ( `.appx` ) contenant le distribution à déployer. L’URI doit pointer vers une `.appx` archive qui contient un unique `install.tar.gz` dans la racine de l’archive, ou à l’intérieur d’une archive interne `.appx` . Voici quelques exemples de distributions pris en charge :

| Distribution                          | Uri                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Debian GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE Leap 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> Les distributions ARM Linux ne sont actuellement pas pris en charge dans GitHub Codespaces.

### <a name="additional-options"></a>Options supplémentaires

Plusieurs options supplémentaires sont prises en charge :

| Nom                      | Type      | Obligatoire | Valeur                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --WSL-version             | string    | Non       | Version de WSL à utiliser. La valeur par défaut est 2.                                                                                                                                  |
| --après création-commande     | string    | Non       | Commande à exécuter à l’intérieur de l’distribution Linux une fois l’installation terminée. La commande doit être mise en forme en tant que mot unique ou placée entre guillemets. La valeur par défaut est no Command.  |

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `wsl-install` outil est d’erreur, car la `input` propriété, distribution à installer, est obligatoire.

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and echo 'Hello from Ubuntu!' after installing.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

---
title: OpenCV
description: Exemple de personnalisation à l’aide de devinit pour cibler à la fois Linux et Windows pour le référentiel OpenCV.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 319f560e4661f12acbef941692e5fd2c257c25ee
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672466"
---
# <a name="opencv"></a>OpenCV

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

Cet exemple montre comment personnaliser [GitHub Codespaces](https://github.com/features/codespaces) afin de développer des projets multiplateformes, tels que [OpenCV/OpenCV](https://github.com/opencv/opencv).

Les personnalisations suivantes sont déjà appliquées à l’embranchement [Microsoft/OpenCV](https://github.com/microsoft/opencv) et permettent à de créer un ciblage Windows et Ubuntu.

## <a name="customization-with-devcontainerjson-and-devinitjson"></a>Personnalisation avec devcontainer.jssur et devinit.js

Le `.devcontainer` répertoire doit contenir les fichiers suivants :

* devcontainer.json
* devinit.js

### <a name="devcontainerjson"></a>devcontainer.json

Voici le contenu du _devcontainer.jssur_ le fichier.

```json
{
  "postCreateCommand": "devinit init"
}
```

Le `postCreateCommand` lance l’outil  [devinit](devinit-and-codespaces.md) , qui consomme _devinit.js_.

### <a name="devinitjson"></a>devinit.js

Voici le contenu du [_devinit.jssur_](devinit-json.md) le fichier.

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages useful for C++ development.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

Le _devinit.jssur_ est le fichier utilisé par l’outil [devinit](devinit-and-codespaces.md) et il doit se trouver dans le même répertoire de _devcontainer.js_.

Dans cet exemple, l’outil [WSL-install](tool-wsl-install.md) est utilisé pour créer une instance WSL exécutant Ubuntu 20,04 et en l’approvisionnant avec les outils de développement C++ essentiels.
## <a name="targeting-windows-or-linux"></a>Ciblage de Windows ou Linux

Une configuration de build ciblant les fenêtres par défaut est toujours nommée `x64-Debug` .

En ajoutant les fichiers mentionnés ci-dessus, lors de la création de l’instance codeSpace, Visual Studio configure une nouvelle connexion SSH dans le [Gestionnaire de connexions](/cpp/linux/connect-to-your-remote-linux-computer)et crée une nouvelle configuration dans le sélecteur de configuration qui cible l’instance Ubuntu via la connexion SSH.

![Configuration ciblant Ubuntu](media/wsl-ssh-linux-configuration.png).

En sélectionnant la configuration mise en surbrillance qui cible WSL, il est possible de générer et déboguer les cibles de génération du OpenCV.

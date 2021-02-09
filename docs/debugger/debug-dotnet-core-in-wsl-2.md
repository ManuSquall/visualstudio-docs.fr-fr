---
title: Déboguer des applications .NET Core dans WSL 2
description: Apprenez à exécuter et déboguer vos applications .NET Core dans WSL 2 sans quitter Visual Studio.
ms.date: 01/25/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 6ae43b79b9db766d752a25fb538b7f208e6f5e13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865616"
---
# <a name="debug-net-core-apps-in-wsl-2-with-visual-studio"></a>Déboguer des applications .NET Core dans WSL 2 avec Visual Studio

Vous pouvez facilement exécuter et déboguer vos applications .NET Core dans Linux sans quitter Visual Studio à l’aide de WSL 2. Si vous êtes un développeur multiplateforme, vous pouvez utiliser cette méthode comme un moyen simple de tester davantage vos environnements cibles.

Pour un utilisateur Windows .NET ciblant Linux, WSL 2 vit en un point de vue idéal entre le réalisme de production et la productivité. Dans Visual Studio, vous pouvez déjà déboguer dans un environnement Linux distant à l’aide du [débogueur distant](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md), ou avec des conteneurs à l’aide des [outils de conteneur](../containers/overview.md). Lorsque le réalisme de la production est votre préoccupation principale, vous devez utiliser l’une de ces options. Lorsqu’une boucle interne simple et rapide est plus importante, WSL 2 est une option intéressante.

Vous n’êtes pas obligé de choisir une seule méthode ! Vous pouvez avoir un profil de lancement pour l’ancrage et le WSL 2 dans le même projet et choisir celui qui convient à une exécution particulière. Une fois votre application déployée, vous pouvez toujours utiliser le débogueur distant pour s’y attacher en cas de problème.

## <a name="prerequisites"></a>Prérequis

- Visual Studio 2019 v 16.9 Preview 1 ou versions ultérieures avec le composant facultatif débogage .NET Core avec WSL 2.

  Le composant facultatif est inclus par défaut dans les charges de travail multiplateforme .NET Core ou ASP.NET et développement Web. Vous devez installer l’une de ces charges de travail ou les deux.

- Installez [WSL 2](/windows/wsl/about).

- Installez la [distribution](https://aka.ms/wslstore) de votre choix.

## <a name="start-debugging-with-wsl-2"></a>Démarrer le débogage avec WSL 2

1. Une fois que vous avez installé les composants requis, ouvrez une application Web ASP.NET Core ou une application console .NET Core dans Visual Studio. un nouveau profil de lancement nommé WSL 2 s’affiche :

   ![Profil de lancement WSL 2 dans la liste des profils de lancement](media/linux-wsl2-debugging-select-launch-profile.png)

1. Sélectionnez ce profil pour l’ajouter à votre *launchSettings.js*.

   Certains des attributs clés du fichier sont affichés dans l’exemple suivant.

    ```json
    "WSL 2": {
        "commandName": "WSL2",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```

   Une fois que vous avez sélectionné le nouveau profil, l’extension vérifie que votre distribution WSL 2 est configurée pour exécuter les applications .NET Core et vous aide à installer toutes les dépendances manquantes. Une fois que vous avez installé ces dépendances, vous êtes prêt à effectuer le débogage dans WSL 2.

1. Démarrez le débogage normalement, et votre application s’exécutera dans votre distribution WSL 2 par défaut.

   Un moyen simple de vérifier que vous exécutez dans Linux consiste à vérifier la valeur de `Environment.OSVersion` .

>[!NOTE]
> Seuls Ubuntu et Debian ont été testés et sont pris en charge. Les autres distributions prises en charge par .NET Core devraient fonctionner, mais nécessitent l’installation manuelle du [Runtime .net Core](https://aka.ms/wsldotnet) et la [boucle](https://curl.haxx.se/).

## <a name="choose-a-specific-distribution"></a>Choisir une distribution spécifique

Par défaut, le profil de lancement WSL 2 utilise la distribution par défaut définie dans *wsl.exe*. Si vous souhaitez que votre profil de lancement cible une distribution spécifique, quelle que soit la valeur par défaut, vous pouvez modifier votre profil de lancement. Par exemple, si vous déboguez une application Web et que vous souhaitez la tester sur Ubuntu 20,04, votre profil de lancement ressemble à ce qui suit :

```json
"WSL 2": {
    "commandName": "WSL2",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```

## <a name="target-multiple-distributions"></a>Cibler plusieurs distributions

Pour aller plus loin, si vous travaillez sur une application qui doit s’exécuter dans plusieurs distributions et que vous souhaitez effectuer un test rapide sur chacune d’elles, vous pouvez avoir plusieurs profils de lancement. Par exemple, si vous avez besoin de tester votre application console sur Debian, Ubuntu 18,04 et Ubuntu 20,04, vous pouvez utiliser les profils de lancement suivants :

```json
"WSL 2 : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL 2 : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL 2 : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```

Grâce à ces profils de lancement, vous pouvez facilement basculer entre vos distributions cibles, tout cela sans quitter Visual Studio.

![Plusieurs profils de lancement WSL 2 dans la liste des profils de lancement](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Paramètres WSL dans le profil de lancement

Le tableau suivant indique les paramètres qui sont pris en charge dans le profil de lancement.

|Nom|Default|Objectif|Prend en charge les jetons ?|
|-|-|-|-|
|executablePath|dotnet|Exécutable à exécuter|Oui|
|commandLineArgs|Valeur de la propriété MSBuild TargetPath mappée à l’environnement WSL|Arguments de ligne de commande passés à executablePath|Oui|
|workingDirectory|Pour les applications console : {*OutDir*}</br>Pour les applications Web : {*ProjectDir*}|Répertoire de travail dans lequel démarrer le débogage|Oui|
|environmentVariables||Paires clé-valeur de variables d’environnement à définir pour le processus débogué.|Oui|
|setupScriptPath||Script à exécuter avant le débogage. Utile pour l’exécution de scripts comme ~/.bash_profile.|Oui|
|distributionName||Nom de la distribution WSL à utiliser.|Non|
|launchBrowser|false|Indique s’il faut ou non lancer un navigateur|Non|
|launchUrl||URL à lancer si launchBrowser a la valeur true|Non|

Jetons pris en charge :

{*ProjectDir*} : chemin d’accès au répertoire du projet

{*OutDir*}-la valeur de la propriété MSBuild `OutDir`

>[!NOTE]
> Tous les chemins d’accès sont pour WSL not Windows.

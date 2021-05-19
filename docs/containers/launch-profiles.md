---
title: Gérer les profils de lancement pour les projets Docker Compose
description: Découvrez comment utiliser Docker Compose profils de lancement et contrôler les services qui sont lancés lorsque vous utilisez Docker Compose dans Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 003205525f883b010f897e6e47d4cab92a31b8a1
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110018529"
---
# <a name="manage-launch-profiles-for-docker-compose-preview"></a>Gérer les profils de lancement pour Docker Compose (version préliminaire)

Si vous avez une application qui se compose de plusieurs services et qui utilise Docker Compose, vous pouvez configurer les services qui sont exécutés et débogués en créant ou en modifiant un profil de lancement existant dans Docker Compose paramètres de lancement. Les profils de lancement vous permettent d’exécuter de manière dynamique uniquement les services importants pour votre scénario actuel. Vous pouvez créer et sélectionner des profils de lancement afin de personnaliser votre expérience de débogage et définir des actions de lancement spécifiques telles que `Browser Launch URL` . Vous aurez également la possibilité de choisir chaque service individuellement ou de choisir un profil de Docker Compose, qui examine également votre fichier compose pour déterminer le groupe de services à exécuter.

Pour plus d’informations sur les profils de Docker Compose, consultez [utilisation de profils avec compose](https://docs.docker.com/compose/profiles/).
 
## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019 version 16,10 Preview](https://visualstudio.microsoft.com/vs/preview/) ou version ultérieure
- Solution avec [orchestration de conteneur avec docker compose](tutorial-multicontainer.md)

## <a name="manage-launch-settings"></a>Gérer les paramètres de lancement

Considérez le projet de Docker Compose suivant dans lequel *docker-compose. yml* contient cinq services et trois profils compose (Web, web1 et web2).

```yml
version: '3.9'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    profiles: [web, web1]
    build:
      context: .
      dockerfile: WebApplication1/Dockerfile

  webapplication2:
    image: ${DOCKER_REGISTRY-}webapplication2
    profiles: [web, web2]
    build:
      context: .
      dockerfile: WebApplication2/Dockerfile

  webapplication3:
    image: ${DOCKER_REGISTRY-}webapplication3
    profiles: [web]
    build:
      context: .
      dockerfile: WebApplication3/Dockerfile

  external1:
    image: redis

  external2:
    image: redis

```

Il existe quelques options pour ouvrir la boîte de dialogue Docker Compose paramètres de lancement :
- Dans Visual Studio, choisissez **Déboguer**  >  **gérer docker compose paramètres de lancement**:

    ![Capture d’écran de l’élément de menu Déboguer gérer les paramètres compose](media/launch-settings/debug-dropdown-manage-compose.png)

- Cliquez avec le bouton droit sur le `docker-compose` projet Visual Studio, puis sélectionnez **gérer docker compose paramètres de lancement**

    ![Capture d’écran de l’élément de menu contextuel](media/launch-settings/launch-settings-context-menu.png)

- Utilisez la commande lancement rapide (**CTRL** + **Q**) et recherchez **docker compose** pour trouver la commande ci-dessus.

Dans l’exemple ci-dessous, le `web1` Profil compose est sélectionné, ce qui permet de filtrer la liste des **services** sur les trois sur cinq inclus dans ce profil :

![« Capture d’écran de la boîte de dialogue Paramètres de lancement »](media/launch-settings/launch-settings-create-profile.png)

La section profils Docker Compose s’affiche uniquement si des profils sont définis dans vos fichiers *docker-compose. yml* .

L’exemple suivant illustre la sélection d’un service à un autre au lieu de filtrer les services d’un profil compose. Ici, nous montrons comment la boîte de dialogue se présenterait si vous avez créé un nouveau profil de lancement nommé `test2` qui démarre uniquement deux des cinq services, `webapplication1` avec débogage et `webapplication2` sans débogage.  Ce profil de lancement lance également un navigateur lorsque l’application démarre et l’ouvre sur la page d’hébergement de `webapplication1` . 

![Capture d’écran de la boîte de dialogue Paramètres de lancement avec certains services désélectionnés](media/launch-settings/launch-settings-selected.png)

Ces informations seront enregistrées dans *launchSettings.js* , comme indiqué ci-dessous.

```json
{
    "profiles": {
      "test2": {
        "commandName": "DockerCompose",
        "composeLaunchServiceName": "webapplication1",
        "serviceActions": {
          "external1": "DoNotStart",
          "external2": "DoNotStart",
          "webapplication1": "StartDebugging",
          "webapplication2": "StartWithoutDebugging",
          "webapplication3": "DoNotStart"
        },
        "composeLaunchAction": "LaunchBrowser",
        "commandVersion": "1.0",
        "composeLaunchUrl": "{Scheme}://localhost:{ServicePort}"
      }
   }
}
```

## <a name="create-a-launch-profile-that-uses-a-docker-compose-profile"></a>Créer un profil de lancement qui utilise un profil de Docker Compose

Vous pouvez également personnaliser davantage les comportements de lancement en créant des profils de lancement Visual Studio qui utilisent les profils compose.

Pour créer un autre profil qui utilise le profil compose, sélectionnez utiliser des **profils de docker compose** et choisissez `web1` . Le profil de lancement comprend désormais trois services `webapplication1` (qui appartiennent aux `web` profils et les `web1` profils compose), `external1` et `external2` . Par défaut, les services sans code source, tels que `external1` et,  `external2` ont l’action par défaut **exécuter sans débogage**. Par défaut, les applications .NET avec le code source **démarrent le débogage**.

> [!IMPORTANT]
> Si un service ne spécifie pas de profil compose, il est inclus dans tous les profils compose de manière implicite.

![Capture d’écran de la boîte de dialogue Paramètres de lancement avec un autre profil créé](media/launch-settings/launch-settings-create-profile.png)

Ces informations seront enregistrées comme indiqué dans le code suivant. La configuration du service et son action par défaut ne sont pas enregistrées, sauf si vous modifiez l’action par défaut.

```json
{
  "profiles": {
    "test1": {
      "commandName": "DockerCompose",
      "composeProfile": {
         "includes": [
            "web1"
         ]
      },
      "commandVersion": "1.0"
    }
  }
}
```

Vous pouvez également modifier l’action de WebApplication1 pour **Démarrer sans débogage**. Dans *launchSettings.js* , les paramètres se présentent comme suit :

```json
{
  "profiles": {
    "test1": {
        "commandName": "DockerCompose",
        "composeProfile": {
          "includes": [
              "web1"
              ],
          "serviceActions": {
              "webapplication1": "StartWithoutDebugging"
          }
        },
    "commandVersion": "1.0"
    }
  }
}
```

## <a name="properties"></a>Propriétés

Voici une description de chaque propriété dans la *launchSettings.jssur*:

|Propriété| Description|
| - | - |
|commandName| Nom de la commande. La valeur par défaut est « DockerCompose ».|
|commandVersion| Numéro de version utilisé pour gérer le schéma du profil de lancement DockerCompose.|
|composeProfile| Propriété parent qui définit la définition du profil de lancement. Ses propriétés enfants sont `includes` et `serviceActions`|
|composeProfile-comprend | Liste des noms de profil compose qui composent un profil de lancement.|
|composeProfile-serviceActions | Répertorie les profils compose, les services et l’action de lancement sélectionnés pour chaque service.|
|serviceActions | Répertorie les services sélectionnés et l’action de lancement.|
|composeLaunchServiceName| Si DockerLaunchAction ou DockerLaunchBrowser est spécifié, DockerServiceName est le nom du service qui doit être lancé. Utilisez cette propriété pour déterminer quel service dans le Docker Compose fichier sera lancé.|
|composeLaunchAction| Spécifie l’action de lancement à exécuter sur **F5** ou sur **CTRL** + **F5**. Les valeurs autorisées sont None, LaunchBrowser et LaunchWCFTestClient.|
|composeLaunchUrl| URL à utiliser lors du lancement du navigateur. Les jetons de remplacement valides sont « {ServiceIPAddress} », « {ServicePort} » et « {Scheme} ». Par exemple : {Scheme}://{ServiceIPAddress} : {ServicePort}|

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le fonctionnement des outils de conteneur, consultez [vue d’ensemble de la génération et du débogage des outils de conteneur Visual Studio](container-build.md).

## <a name="see-also"></a>Voir aussi

- [Paramètres de lancement des outils de conteneur Visual Studio](container-launch-settings.md)

- [Docker Compose les paramètres de build](docker-compose-properties.md)

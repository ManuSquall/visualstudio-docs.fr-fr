---
title: Paramètres de lancement de Visual Studio Container Tools
author: ghogen
description: Aperçu du processus de construction des outils de conteneurs
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 1c9786c29573da3b0149a9ec6578f2ce58c4de9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76542592"
---
# <a name="container-tools-launch-settings"></a>Paramètres de lancement d’outils de conteneurs

Dans le dossier *Propriétés* dans un projet ASP.NET Core, vous pouvez trouver le fichier launchSettings.json, qui contient des paramètres qui contrôlent la façon dont votre application web est lancée sur votre machine de développement. Pour obtenir des informations détaillées sur la façon dont ce fichier est utilisé dans ASP.NET développement, voir [Utiliser plusieurs environnements dans ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). Dans *launchSettings.json*, les paramètres de la section **Docker** sont liés à la façon dont Visual Studio gère les applications conteneurisées.

::: moniker range="vs-2017"
```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"
    }
```

::: moniker-end
::: moniker range=">=vs-2019"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}",
      "environmentVariables": {
        "ASPNETCORE_URLS": "https://+:443;http://+:80",
        "ASPNETCORE_HTTPS_PORT": "44360"
      },
      "httpPort": 51803,
      "useSSL": true,
      "sslPort": 44360
    }
```

::: moniker-end

Le paramètre commandName indique que cette section s’applique aux outils de conteneurs. Le tableau suivant montre les propriétés qui peuvent être définies dans cette section :

::: moniker range="vs-2017"

|Nom du paramètre|Version| Exemple|Description|
|------------|-------|-------|---------------|
|lancementBrowser|Visual Studio 2017|"launchBrowser": vrai|Indique s’il faut lancer le navigateur après avoir lancé avec succès le projet.|
|lancementUrl|Visual Studio 2017|"launchUrl": "'Scheme’http’ServiceHost': 'ServicePort'"|Cette URL est utilisée lors du lancement du navigateur.  Les jetons de remplacement pris en charge pour cette chaîne sont :<br>   "Scheme" - Remplacé par "http" ou "https" selon que SSL est utilisé.<br>   "ServiceHost" - Habituellement remplacé par "localhost". Lors du ciblage des conteneurs Windows sur Windows 10 RS3 ou plus, cependant, il est remplacé par IP du conteneur.<br>   "ServicePort" - Habituellement remplacé par sslPort ou httpPort, selon que SSL est utilisé.  Lors du ciblage des conteneurs Windows sur Windows 10 RS3 ou plus, cependant, il est remplacé par soit "443" ou "80", selon que SSL est utilisé.|

::: moniker-end

::: moniker range=">=vs-2019"

| Nom du paramètre         |  Exemple                                               | Description                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| commandeLineArgs      | "commandLineArgs": "--mysetting myvalue"              | Ces arguments de ligne de commande sont utilisés lors du lancement de votre projet dans le conteneur.                                     |
| environmentVariables | "environnementVariables":                             | Ces valeurs variables de l’environnement sont transmises au processus lorsqu’il est lancé dans le conteneur.                       |
|                      | "ASPNETCORE_URLS": "https://+:443; http://+:80",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort (en)             | "httpPort": 24051                                     | Ce port sur l’hôte est cartographié au port du conteneur 80 lors du lancement du conteneur.                                |
|                      |                                                       | Si elle n’est pas spécifiée, la valeur est tirée de la valeur de l’iisSettings.                                                          |
| lancementBrowser        | "launchBrowser": vrai                                 | Indique s’il faut lancer le navigateur après avoir lancé avec succès le projet.                                       |
| lancementUrl            | "launchUrl": "'Scheme’http’ServiceHost': 'ServicePort'" | Cette URL est utilisée lors du lancement du navigateur. Les jetons de remplacement pris en charge pour cette chaîne sont :                          |
|                      |                                                       | - "Scheme" - Remplacé par "http" ou "https" selon que SSL est utilisé.                                   |
|                      |                                                       | - 'ServiceHost' - Habituellement remplacé par "localhost".                                                                    |
|                      |                                                       | Lors du ciblage des conteneurs Windows sur Windows 10 RS3 ou plus, cependant, il est remplacé par IP du conteneur.           |
|                      |                                                       | - 'ServicePort' - Habituellement remplacé par sslPort ou httpPort, selon que SSL est utilisé.                   |
|                      |                                                       | Lors du ciblage des conteneurs Windows sur Windows 10 RS3 ou plus, cependant, il est remplacé par soit "443" ou "80",         |
|                      |                                                       | selon que SSL est utilisé.                                                                                       |
| sslPort (en anglais)              | "sslPort": 44381                                      | Ce port sur l’hôte est cartographié au port du conteneur 443 lors du lancement du conteneur.                               |
|                      |                                                       | Si elle n’est pas spécifiée, la valeur est tirée de la valeur de l’iisSettings.                                                          |
| utilisationSSL               | "useSSL": vrai                                        | Indique s’il faut utiliser SSL lors du lancement du projet. Si l’utilisation deSSL n’est pas spécifiée, alors SSL est utilisé lorsque sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Configurez votre projet en définissant les [propriétés de construction d’outils conteneurs.](container-msbuild-properties.md)

## <a name="see-also"></a>Voir aussi

[Docker Compose construit des propriétés](docker-compose-properties.md)

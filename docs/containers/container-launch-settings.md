---
title: Paramètres de lancement des outils de conteneur Visual Studio
author: ghogen
description: En savoir plus sur les paramètres de lancement des outils de conteneur liés à la façon dont Visual Studio gère les applications en conteneur.
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: e50935145913bcd1f3c4457f4704376a0ac0f6ef
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973237"
---
# <a name="container-tools-launch-settings"></a>Paramètres de lancement des outils de conteneur

Dans le dossier *Propriétés* d’un projet ASP.net Core, vous trouverez le launchSettings.jssur le fichier, qui contient des paramètres qui contrôlent la façon dont votre application Web est démarrée sur votre ordinateur de développement. Pour plus d’informations sur l’utilisation de ce fichier dans le développement ASP.NET, consultez [utiliser plusieurs environnements dans ASP.net Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2&preserve-view=true). Dans *launchSettings.jssur*, les paramètres de la section de l' **ancrage** sont liés à la façon dont Visual Studio gère les applications en conteneur.

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

Le paramètre commandName indique que cette section s’applique aux outils de conteneur. Le tableau suivant présente les propriétés qui peuvent être définies dans cette section :

::: moniker range="vs-2017"

|Nom du paramètre|Version|Exemple|Description|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|« launchBrowser » : true|Indique s’il faut lancer le navigateur après avoir correctement lancé le projet.|
|launchUrl|Visual Studio 2017|« launchUrl » : « {Scheme}://{ServiceHost} : {ServicePort} »|Cette URL est utilisée lors du lancement du navigateur.  Les jetons de remplacement pris en charge pour cette chaîne sont les suivants :<br>   {Scheme} : remplacé par « http » ou « https » selon que le protocole SSL est utilisé ou non.<br>   {ServiceHost} : généralement remplacé par « localhost ». Toutefois, lorsque vous ciblez des conteneurs Windows sur Windows 10 RS3 ou une version antérieure, elles sont remplacées par l’adresse IP du conteneur.<br>   {ServicePort} : généralement remplacé par sslPort ou httpPort, selon que le protocole SSL est utilisé ou non.  Toutefois, lorsque vous ciblez des conteneurs Windows sur Windows 10 RS3 ou une version antérieure, elles sont remplacées par « 443 » ou « 80 », selon que le protocole SSL est utilisé ou non.|

::: moniker-end

::: moniker range=">=vs-2019"

| Nom du paramètre         | Exemple                                               | Description                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| commandLineArgs      | « commandLineArgs » : « --MySetting MyValue »              | Ces arguments de ligne de commande pour le démarrage de votre application sont utilisés lors du lancement de votre projet dans le conteneur.                                     |
| environmentVariables | « environmentVariables » : {                             | Ces valeurs de variable d’environnement sont passées au processus lorsqu’il est lancé dans le conteneur.                       |
|                      | « ASPNETCORE_URLS » : « https://+:443 ; http://+:80 »,       |                                                                                                                         |
|                      | « ASPNETCORE_HTTPS_PORT » : « 44381 »                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | « httpPort » : 24051                                     | Ce port sur l’hôte est mappé au port 80 du conteneur lors du lancement du conteneur.                                |
|                      |                                                       | S’il n’est pas spécifié, la valeur est extraite de la valeur iisSettings.                                                          |
| launchBrowser        | « launchBrowser » : true                                 | Indique s’il faut lancer le navigateur après avoir correctement lancé le projet.                                       |
| launchUrl            | « launchUrl » : « {Scheme}://{ServiceHost} : {ServicePort} » | Cette URL est utilisée lors du lancement du navigateur. Les jetons de remplacement pris en charge pour cette chaîne sont les suivants :                          |
|                      |                                                       | -{Scheme} : remplacé par « http » ou « https » selon que le protocole SSL est utilisé ou non.                                   |
|                      |                                                       | -{ServiceHost} : généralement remplacé par « localhost ».                                                                    |
|                      |                                                       | Toutefois, lorsque vous ciblez des conteneurs Windows sur Windows 10 RS3 ou une version antérieure, elles sont remplacées par l’adresse IP du conteneur.           |
|                      |                                                       | -{ServicePort}-généralement remplacé par sslPort ou httpPort, selon que le protocole SSL est utilisé ou non.                   |
|                      |                                                       | Toutefois, lorsque vous ciblez des conteneurs Windows sur Windows 10 RS3 ou une version antérieure, il est remplacé par « 443 » ou « 80 ».         |
|                      |                                                       | selon que le protocole SSL est utilisé ou non.                                                                                       |
| sslPort              | « sslPort » : 44381                                      | Ce port sur l’hôte est mappé au port 443 du conteneur lors du lancement du conteneur.                               |
|                      |                                                       | S’il n’est pas spécifié, la valeur est extraite de la valeur iisSettings.                                                          |
| useSSL               | « useSSL » : true                                        | Indique s’il faut utiliser SSL lors du lancement du projet. Si useSSL n’est pas spécifié, SSL est utilisé lorsque sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Configurez votre projet en définissant les [Propriétés de build des outils de conteneur](container-msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

- [Docker Compose les propriétés de build](docker-compose-properties.md)
- [Gérer les profils de lancement pour Docker Compose](launch-profiles.md)

---
title: Publish-WebApplicationVM | Microsoft Docs
description: Découvrez comment déployer une application web sur une machine virtuelle. Ce script crée les ressources requises dans votre abonnement Azure si elles n’existent pas.
author: ghogen
manager: jillfra
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: dd7102873047ed7331547225fa0b32efd33f853f
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508416"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (script Windows PowerShell)
Déploie une application web sur un ordinateur virtuel. Le script crée les ressources requises dans votre abonnement Azure si elles n’existent pas.

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Configuration
Le chemin d'accès au fichier de configuration JSON qui décrit les détails du déploiement.

| Alias | aucun |
| --- | --- |
| Nécessaire ? |true |
| Position |nommée |
| Valeur par défaut |aucun |
| Accepter l'entrée de pipeline ? |false |
| Accepter les caractères génériques ? |false |

### <a name="subscriptionname"></a>SubscriptionName
Nom de l’abonnement Azure dans lequel vous souhaitez créer la machine virtuelle.

| Alias | aucun |
| --- | --- |
| Nécessaire ? |false |
| Position |nommée |
| Valeur par défaut |Utilise le premier abonnement dans le fichier d’abonnement |
| Accepter l'entrée de pipeline ? |false |
| Accepter les caractères génériques ? |false |

### <a name="webdeploypackage"></a>WebDeployPackage
Le chemin d’accès au package de déploiement web à publier sur la machine virtuelle. Vous pouvez créer ce package à l'aide de l'Assistant Publier le site web dans Visual Studio. Consultez [Création d’un package de déploiement web dans Visual Studio](/previous-versions/aspnet/dd465323(v=vs.110)).

| Alias | aucun |
| --- | --- |
| Nécessaire ? |false |
| Position |nommée |
| Valeur par défaut |aucun |
| Accepter l'entrée de pipeline ? |false |
| Accepter les caractères génériques ? |false |

### <a name="allowuntrusted"></a>AllowUntrusted
Si la valeur est true, autorise l’utilisation de certificats qui ne sont pas signés par une autorité racine approuvée.

| Alias | aucun |
| --- | --- |
| Nécessaire ? |false |
| Position |nommée |
| Valeur par défaut |false |
| Accepter l'entrée de pipeline ? |false |
| Accepter les caractères génériques ? |false |

### <a name="vmpassword"></a>VMPassword
Informations d’identification de votre compte de machine virtuelle. Exemple : -VMPassword @{Name = "admin"; Password = "mdp"}

| Alias | aucun |
| --- | --- |
| Nécessaire ? |false |
| Position |nommée |
| Valeur par défaut |aucun |
| Accepter l'entrée de pipeline ? |false |
| Accepter les caractères génériques ? |false |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Informations d’identification de la base de données SQL Azure. Exemple : -DatabaseServerPassword @{Name = "admin"; Password = "mdp"}

| Alias | aucun |
| --- | --- |
| Nécessaire ? |false |
| Position |nommée |
| Valeur par défaut |aucun |
| Accepter l'entrée de pipeline ? |false |
| Accepter les caractères génériques ? |false |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Si true, imprime des messages à partir du script dans le flux de sortie.

| Alias | aucun |
| --- | --- |
| Nécessaire ? |false |
| Position |nommée |
| Valeur par défaut |false |
| Accepter l'entrée de pipeline ? |false |
| Accepter les caractères génériques ? |false |

## <a name="remarks"></a>Remarques
Pour obtenir une explication complète de la façon d'utiliser le script pour créer des environnements de développement et de test, consultez [Utilisation des scripts Windows PowerShell pour la publication dans des environnements de développement et de test](vs-azure-tools-publishing-using-powershell-scripts.md).

Le fichier de configuration JSON spécifie les détails de ce qui doit être déployé. Il inclut les informations que vous avez spécifiées lorsque vous avez créé le projet, comme le nom, le groupe d’affinités, l’image VHD et la taille de la machine virtuelle. Il inclut également les points de terminaison sur la machine virtuelle, les bases de données à configurer, le cas échéant, et les paramètres de déploiement web. Le code suivant montre un exemple de fichier de configuration JSON :

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Vous pouvez modifier le fichier de configuration JSON pour modifier ce qui est configuré. Une machine virtuelle et un service cloud sont requis, mais la section de la base de données est facultative.
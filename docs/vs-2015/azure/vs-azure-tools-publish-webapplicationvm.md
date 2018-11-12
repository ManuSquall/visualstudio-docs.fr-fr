---
title: Publish-WebApplicationVM | Microsoft Docs
description: Découvrez comment déployer une application web à une machine virtuelle. Ce script crée les ressources requises dans votre abonnement Azure si elles n’existent pas.
author: ghogen
manager: douge
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: c2383e6d7b14d801a391a725f0482736fb926cd1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002043"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (script Windows PowerShell)
Déploie une application web à une machine virtuelle. Le script crée les ressources requises dans votre abonnement Azure si elles n’existent pas.

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
Le chemin d’accès au fichier de configuration JSON qui décrit les détails du déploiement.

| Alias | none |
| --- | --- |
| Obligatoire ? |true |
| Position |nommés |
| Valeur par défaut |none |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

### <a name="subscriptionname"></a>SubscriptionName
Le nom de l’abonnement Azure dans lequel vous souhaitez créer la machine virtuelle.

| Alias | none |
| --- | --- |
| Obligatoire ? |False |
| Position |nommés |
| Valeur par défaut |Utilise le premier abonnement dans le fichier d’abonnement |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

### <a name="webdeploypackage"></a>WebDeployPackage
Le chemin d’accès au package de déploiement web pour publier sur la machine virtuelle. Vous pouvez créer ce package à l’aide de l’Assistant Publier le site Web dans Visual Studio. Consultez [Comment : créer un Package de déploiement Web dans Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx).

| Alias | none |
| --- | --- |
| Obligatoire ? |False |
| Position |nommés |
| Valeur par défaut |none |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

### <a name="allowuntrusted"></a>AllowUntrusted
Si la valeur est true, autoriser l’utilisation de certificats qui ne sont pas signés par une autorité racine approuvée.

| Alias | none |
| --- | --- |
| Obligatoire ? |False |
| Position |nommés |
| Valeur par défaut |False |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

### <a name="vmpassword"></a>VMPassword
Les informations d’identification pour le compte d’ordinateur virtuel. Exemple : - VMPassword @{nom = « admin » ; Mot de passe = « MDP »}

| Alias | none |
| --- | --- |
| Obligatoire ? |False |
| Position |nommés |
| Valeur par défaut |none |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Les informations d’identification pour la base de données SQL Azure. Exemple : - DatabaseServerPassword @{nom = « admin » ; Mot de passe = « MDP »}

| Alias | none |
| --- | --- |
| Obligatoire ? |False |
| Position |nommés |
| Valeur par défaut |none |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Si la valeur est true, imprime des messages à partir du script dans le flux de sortie.

| Alias | none |
| --- | --- |
| Obligatoire ? |False |
| Position |nommés |
| Valeur par défaut |False |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="remarks"></a>Notes
Pour obtenir une explication complète de la façon d’utiliser le script pour créer des environnements de développement et de Test, consultez [à l’aide de Scripts Windows PowerShell pour publier sur le développement et les environnements de Test](vs-azure-tools-publishing-using-powershell-scripts.md).

Le fichier de configuration JSON spécifie les détails de ce qui doit être déployé. Il inclut les informations que vous avez spécifié lorsque vous avez créé le projet, comme le nom, groupe d’affinités, image de disque dur virtuel et la taille de la machine virtuelle. Il inclut également les points de terminaison sur la machine virtuelle, les bases de données à configurer, le cas échéant et les paramètres de déploiement web. Le code suivant montre un exemple de fichier de configuration JSON :

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


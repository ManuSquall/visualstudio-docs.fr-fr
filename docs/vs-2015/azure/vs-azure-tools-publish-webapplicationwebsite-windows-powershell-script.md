---
title: Publish-WebApplicationWebSite (script Windows PowerShell) | Microsoft Docs
description: Découvrez comment publier un projet web sur un site Web Azure. Ce script crée les ressources requises dans votre abonnement Azure si elles n’existent pas.
author: ghogen
manager: douge
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 175181d5d866e9d7fab51eaf7c3262e47d0ed6a8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001977"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (script Windows PowerShell)
## <a name="syntax"></a>Syntaxe
Publie un projet web sur un site Web Azure. Le script crée les ressources requises dans votre abonnement Azure si elles n’existent pas.

    Publish-WebApplicationWebSite
    –Configuration <configuration>
    -SubscriptionName <subscriptionName>
    -WebDeployPackage <packageName>
    -DatabaseServerPassword @{Name = "name"; Password = "password"}
    -SendHostMessagesToOutput
    -Verbose


## <a name="configuration"></a>Configuration
Le chemin d’accès au fichier de configuration JSON qui décrit les détails du déploiement.

| Paramètre | Valeur par défaut |
| --- | --- |
| Alias |none |
| Obligatoire ? |true |
| Position |nommés |
| Valeur par défaut |none |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="subscriptionname"></a>SubscriptionName
Le nom de l’abonnement Azure que vous souhaitez créer le site Web dans.

| Paramètre | Valeur par défaut |
| --- | --- |
| Alias |none |
| Obligatoire ? |False |
| Position |nommés |
| Valeur par défaut |none |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="webdeploypackage"></a>WebDeployPackage
Le chemin d’accès au package de déploiement web pour publier sur le site Web. Vous pouvez créer ce package à l’aide de l’Assistant Publier le site Web dans Visual Studio. Pour plus d’informations, consultez [prise en main Azure Cloud Services et ASP.NET](http://go.microsoft.com/fwlink/p/?LinkID=623089).

| Paramètre | Valeur par défaut |
| --- | --- |
| Alias |none |
| Obligatoire ? |False |
| Position |nommés |
| Valeur par défaut |none |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Le nom d’utilisateur et un mot de passe pour la base de données SQL Azure.

| Paramètre | Valeur par défaut |
| --- | --- |
| Alias |none |
| Obligatoire ? |False |
| Position |nommés |
| Valeur par défaut |none |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Si la valeur est true, imprime des messages à partir du script dans le flux de sortie.

| Paramètre | Valeur par défaut |
| --- | --- |
| Alias |none |
| Obligatoire ? |False |
| Position |nommés |
| Valeur par défaut |False |
| Accepter l’entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="remarks"></a>Notes
Pour obtenir une explication complète de la façon d’utiliser le script pour créer des environnements de développement et de Test, consultez [à l’aide de Scripts Windows PowerShell pour publier sur le développement et les environnements de Test](vs-azure-tools-publishing-using-powershell-scripts.md).

Le fichier de configuration JSON spécifie les détails de ce qui doit être déployé. Il inclut les informations que vous avez spécifié lorsque vous avez créé le projet, telles que le nom et le nom d’utilisateur pour le site Web. Il inclut également la base de données à la configuration, le cas échéant. Le code suivant montre un exemple de fichier de configuration JSON :

    {
        "environmentSettings": {
            "webSite": {
                "name": "WebApplication10554",
                "location": "West US"
            },
            "databases": [
                {
                    "connectionStringName": "DefaultConnection",
                    "databaseName": "WebApplication10554_db",
                    "serverName": "iss00brc88",
                    "user": "sqluser2",
                    "password": "",
                    "edition": "",
                    "size": "",
                    "collation": "",
                    "location": "West US"
                }
            ]
        }
    }

Vous pouvez modifier le fichier de configuration JSON pour modifier ce qui est déployé. Une section du site Web est requise, mais la section de la base de données est facultative.

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations, consultez [Publish-WebApplicationVM (script Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md)


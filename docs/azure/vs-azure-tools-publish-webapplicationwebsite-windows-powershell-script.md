---
title: Publish-WebApplicationWebSite (script Windows PowerShell) | Microsoft Docs
description: Découvrez comment publier un projet web sur un site web Azure. Ce script crée les ressources requises dans votre abonnement Azure si elles n’existent pas.
services: visual-studio-online
author: ghogen
manager: douge
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
origin.date: 11/11/2016
ms.date: 09/10/2018
ms.author: v-junlch
ms.openlocfilehash: 2e5bd615e83c56a257e093c42fca2a98c5a3efd8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62427440"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (script Windows PowerShell)
## <a name="syntax"></a>Syntaxe
Publie un projet web sur un site web Azure. Le script crée les ressources requises dans votre abonnement Azure si elles n’existent pas.

    Publish-WebApplicationWebSite
    -Configuration <configuration>
    -SubscriptionName <subscriptionName>
    -WebDeployPackage <packageName>
    -DatabaseServerPassword @{Name = "name"; Password = "password"}
    -SendHostMessagesToOutput
    -Verbose


## <a name="configuration"></a>Configuration
Le chemin d'accès au fichier de configuration JSON qui décrit les détails du déploiement.

| Paramètre | Valeur par défaut |
| --- | --- |
| Alias |none |
| Obligatoire ? |true |
| Position |named |
| Valeur par défaut |none |
| Accepter l'entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="subscriptionname"></a>SubscriptionName
Nom de l’abonnement Azure dans lequel vous souhaitez créer le site web.

| Paramètre | Valeur par défaut |
| --- | --- |
| Alias |none |
| Obligatoire ? |False |
| Position |named |
| Valeur par défaut |none |
| Accepter l'entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="webdeploypackage"></a>WebDeployPackage
Le chemin d'accès au package de déploiement web à publier sur le site web. Vous pouvez créer ce package à l'aide de l'Assistant Publier le site web dans Visual Studio. Pour plus d’informations, consultez [Prise en main des services cloud Azure et d'ASP.NET](http://go.microsoft.com/fwlink/p/?LinkID=623089).

| Paramètre | Valeur par défaut |
| --- | --- |
| Alias |none |
| Obligatoire ? |False |
| Position |named |
| Valeur par défaut |none |
| Accepter l'entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Le nom d’utilisateur et le mot de passe pour la base de données SQL dans Azure.

| Paramètre | Valeur par défaut |
| --- | --- |
| Alias |none |
| Obligatoire ? |False |
| Position |named |
| Valeur par défaut |none |
| Accepter l'entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Si true, imprime des messages à partir du script dans le flux de sortie.

| Paramètre | Valeur par défaut |
| --- | --- |
| Alias |none |
| Obligatoire ? |False |
| Position |named |
| Valeur par défaut |False |
| Accepter l'entrée de pipeline ? |False |
| Accepter les caractères génériques ? |False |

## <a name="remarks"></a>Remarques
Pour obtenir une explication complète de la façon d'utiliser le script pour créer des environnements de développement et de test, consultez [Utilisation des scripts Windows PowerShell pour la publication dans des environnements de développement et de test](vs-azure-tools-publishing-using-powershell-scripts.md).

Le fichier de configuration JSON spécifie les détails de ce qui doit être déployé. Il inclut les informations que vous avez spécifiées lorsque vous avez créé le projet, comme le nom et le nom d'utilisateur pour le site web. Il inclut également la base de données à configurer, le cas échéant. Le code suivant montre un exemple de fichier de configuration JSON :

    {
        "environmentSettings": {
            "webSite": {
                "name": "WebApplication10554",
                "location": "China North"
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
                    "location": "China North"
                }
            ]
        }
    }

Vous pouvez modifier le fichier de configuration JSON pour modifier ce qui est déployé. Une section de site web est requise, mais la section de la base de données est facultative.

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations, consultez [Publish-WebApplicationVM (script Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md)


<!-- Update_Description: update metedata properties -->
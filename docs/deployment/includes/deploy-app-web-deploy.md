---
title: Déployer à l’aide de Web Deploy
description: Déployer une application à l’aide de Web Deploy dans Visual Studio
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38811920"
---
Si vous avez installé le Web Deploy à l’aide de Web Platform Installer, vous pouvez déployer l’application directement à partir de Visual Studio.

1. Démarrez Visual Studio avec des privilèges d’administrateur et rouvrez le projet.

    Privilèges d’administrateur sont requis pour déployer votre application à l’aide de Web Deploy.

1. Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet et sélectionnez **Publier**.

    Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche. Cliquez sur **nouveau profil**.

1. Pour **sélectionner une cible de publication**, sélectionnez **IIS, FTP, etc.** et cliquez sur **publier**.

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Entrez les paramètres de configuration de correction pour l’installation d’IIS.

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Si un nom d’hôte ne résout pas lorsque vous essayez de valider en suivant les étapes le **Server** texte boîte, essayez de l’adresse IP. Inclure `http://` en tant que préfixe dans le **Server** champ.  Vérifiez que vous utilisez le port 80 dans le **Server** texte zone et vous assurer que les ports 80 et 8172 sont ouverts dans le pare-feu.

1. Choisissez **valider**. Si le programme d’installation de la connexion est valide, vous pouvez essayer de publier.

1. Cliquez sur **publier** pour publier l’application.

    L’onglet sortie vous indique si la publication est réussie et que votre navigateur puis ouvre l’application.

    Si vous obtenez une erreur mentionnant Web Deploy, vérifiez à nouveau les étapes d’installation Web Deploy et vérifiez que les ports appropriés sont ouverts (Web Deploy requiert également le port 8172 soient ouverts sur le serveur).

    Si l’application se déploie correctement, mais elle ne s’exécute pas correctement, il peut y avoir un problème avec votre configuration d’IIS, votre installation d’ASP.NET ou la configuration de votre site Web. Sur le serveur Windows, ouvrez le site Web à partir d’IIS pour les messages d’erreur plus spécifiques et puis revérifiez les étapes précédentes.

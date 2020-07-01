---
title: Déployer dans un dossier local
description: Déployer une application dans un dossier local
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 3fa0569739ee81ec4b2aa0eec8157068ffc949cd
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149217"
---
1. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **publier** (pour Web Forms, **publier l’application Web**).

    Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **nouveau profil**.

1. Dans la boîte de dialogue **publier** , sélectionnez **dossier**, cliquez sur **Parcourir**, puis créez un nouveau dossier, **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Pour une application Web Forms, choisissez **personnalisé** dans la boîte de dialogue publier, entrez un nom de profil, puis choisissez **OK**.

1. Cliquez sur **créer un profil** dans la liste déroulante (**publier** est la valeur par défaut).

1. Dans la boîte de dialogue **publier** , cliquez sur le lien **paramètres** , puis sélectionnez l’onglet **paramètres** .

1. Définissez la configuration sur **Déboguer**, sélectionnez **Supprimer tous les fichiers existants avant la publication**, puis cliquez sur **Enregistrer**.

    > [!NOTE]
    > Si vous utilisez une version Release, vous désactivez le débogage dans le fichier web.config lors de la publication.

1. Cliquez sur **Publier**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")

    L’application publie une configuration **Debug** du projet dans le dossier local. La progression s’affiche dans la fenêtre sortie.

1. Copiez le répertoire du projet ASP.NET à partir de l’ordinateur Visual Studio vers le répertoire local configuré pour l’application ASP.NET (dans cet exemple, **C:\Publish**) sur l’ordinateur Windows Server. Dans ce didacticiel, nous partons du principe que vous copiez manuellement, mais vous pouvez utiliser d’autres outils tels que PowerShell, xcopy ou Robocopy.

    > [!CAUTION]
    > Si vous devez apporter des modifications au code ou à la régénération, vous devez republier et répéter cette étape. Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.    Si vous ne le faites pas, vous recevrez un `cannot find or open the PDB file` avertissement dans Visual Studio lorsque vous tenterez de déboguer le processus.

1. Sur le serveur Windows, vérifiez que vous pouvez exécuter l’application correctement en ouvrant l’application dans votre navigateur.

    Si l’application ne s’exécute pas correctement, il se peut qu’il y ait une incompatibilité entre la version de ASP.NET installée sur votre serveur et votre ordinateur Visual Studio, ou vous avez peut-être un problème avec la configuration de votre site Web ou IIS. Revérifiez les étapes précédentes.

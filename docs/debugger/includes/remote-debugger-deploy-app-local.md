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
ms.openlocfilehash: b6ceee76d8c24ccddb41e47c0865d96c79e6fc32
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249914"
---
1. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **publier** (pour Web Forms, **publier l’application Web**).

    Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **nouveau profil**.

1. Dans la boîte de dialogue **publier** , sélectionnez **dossier**, cliquez sur **Parcourir**, puis créez un nouveau dossier, **C:\Publish**.

   ::: moniker range=">=vs-2019"

   :::image type="content" source="../media/vs-2019/remotedbg-publish-local.png" alt-text="Capture d’écran de la boîte de dialogue choisir une cible de publication dans Visual Studio avec le dossier « C:\Publish » sélectionné en tant que cible de publication.":::

   Cliquez sur **Terminer** pour enregistrer le profil de publication.
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Capture d’écran de la boîte de dialogue choisir une cible de publication dans Visual Studio avec le dossier’bin\Release\Publish’sélectionné en tant que cible de publication.](../media/remotedbg_publish_local.png)
   Pour une application Web Forms, choisissez **personnalisé** dans la boîte de dialogue publier, entrez un nom de profil, puis choisissez **OK**.

   Cliquez sur **créer un profil** dans la liste déroulante (**publier** est la valeur par défaut).
   ::: moniker-end

1. Basculez vers une configuration de débogage.

   ::: moniker range=">=vs-2019"
   Choisissez **modifier** pour modifier le profil, puis choisissez **paramètres**. Choisissez une configuration de **débogage** , puis choisissez **Supprimer les fichiers supplémentaires à la destination** sous les options de publication de **fichier** .
   ::: moniker-end
   ::: moniker range="vs-2017"
   Dans la boîte de dialogue **paramètres** , activez le débogage en cliquant sur **suivant**, choisissez une configuration de **débogage** , puis choisissez **Supprimer les fichiers supplémentaires à la destination** sous les options de publication de **fichier** .
   ::: moniker-end

   > [!NOTE]
   > Si vous utilisez une version Release, vous désactivez le débogage dans le fichier *web.config* lors de la publication.

1. Cliquez sur **Publier**.

    ![Capture d’écran de l’onglet Paramètres de la boîte de dialogue publier. La configuration est définie sur déboguer et le bouton publier est sélectionné.](../media/remotedbg_publish_debug_config.png)

    L’application publie une configuration **Debug** du projet dans le dossier local. La progression s’affiche dans la fenêtre sortie.

1. Copiez le répertoire du projet ASP.NET à partir de l’ordinateur Visual Studio vers le répertoire local configuré pour l’application ASP.NET (dans cet exemple, **C:\Publish**) sur l’ordinateur Windows Server. Dans ce didacticiel, nous partons du principe que vous copiez manuellement, mais vous pouvez utiliser d’autres outils tels que PowerShell, xcopy ou Robocopy.

    > [!CAUTION]
    > Si vous devez apporter des modifications au code ou à la régénération, vous devez republier et répéter cette étape. Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux. Si vous ne le faites pas, vous recevrez un `cannot find or open the PDB file` avertissement dans Visual Studio lorsque vous tenterez de déboguer le processus.

1. Sur le serveur Windows, vérifiez que vous pouvez exécuter l’application correctement en ouvrant l’application dans votre navigateur.

    Si l’application ne s’exécute pas correctement, il se peut qu’il y ait une incompatibilité entre la version de ASP.NET installée sur votre serveur et votre ordinateur Visual Studio, ou vous avez peut-être un problème avec la configuration de votre site Web ou IIS. Revérifiez les étapes précédentes.

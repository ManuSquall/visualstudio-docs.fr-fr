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
ms.openlocfilehash: 1d049bc8b74b83028e04fe92e7ce96f45907d042
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97762599"
---
1. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **publier** (pour Web Forms, **publier l’application Web**).

    Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **nouveau profil**.

1. Dans la boîte de dialogue **publier** , sélectionnez **dossier**, cliquez sur **Parcourir**, puis créez un nouveau dossier, **C:\Publish**.

    ![Capture d’écran de la boîte de dialogue choisir une cible de publication dans Visual Studio avec le dossier’bin\Release\Publish’sélectionné en tant que cible de publication.](../media/remotedbg_publish_local.png)

    Pour une application Web Forms, choisissez **personnalisé** dans la boîte de dialogue publier, entrez un nom de profil, puis choisissez **OK**.

1. Cliquez sur **créer un profil** dans la liste déroulante (**publier** est la valeur par défaut).

1. Dans la boîte de dialogue **publier** , cliquez sur le lien **paramètres** , puis sélectionnez l’onglet **paramètres** .

1. Définissez la configuration sur **Déboguer**, sélectionnez **Supprimer tous les fichiers existants avant la publication**, puis cliquez sur **Enregistrer**.

    > [!NOTE]
    > Si vous utilisez une version Release, vous désactivez le débogage dans le fichier web.config lors de la publication.

1. Cliquez sur **Publier**.

    ![Capture d’écran de l’onglet Paramètres de la boîte de dialogue publier. La configuration est définie sur déboguer et le bouton publier est sélectionné.](../media/remotedbg_publish_debug_config.png)

    L’application publie une configuration **Debug** du projet dans le dossier local. La progression s’affiche dans la fenêtre sortie.

1. Copiez le répertoire du projet ASP.NET à partir de l’ordinateur Visual Studio vers le répertoire local configuré pour l’application ASP.NET (dans cet exemple, **C:\Publish**) sur l’ordinateur Windows Server. Dans ce didacticiel, nous partons du principe que vous copiez manuellement, mais vous pouvez utiliser d’autres outils tels que PowerShell, xcopy ou Robocopy.

    > [!CAUTION]
    > Si vous devez apporter des modifications au code ou à la régénération, vous devez republier et répéter cette étape. Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.    Si vous ne le faites pas, vous recevrez un `cannot find or open the PDB file` avertissement dans Visual Studio lorsque vous tenterez de déboguer le processus.

1. Sur le serveur Windows, vérifiez que vous pouvez exécuter l’application correctement en ouvrant l’application dans votre navigateur.

    Si l’application ne s’exécute pas correctement, il se peut qu’il y ait une incompatibilité entre la version de ASP.NET installée sur votre serveur et votre ordinateur Visual Studio, ou vous avez peut-être un problème avec la configuration de votre site Web ou IIS. Revérifiez les étapes précédentes.

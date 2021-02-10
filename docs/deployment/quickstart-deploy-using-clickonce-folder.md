---
title: Déployer une application de bureau Windows .NET à l’aide de ClickOnce
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5a6f7c2c8d6c79270df94c100bbd4625856efa15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934505"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>Déployer une application de bureau Windows .NET à l’aide de ClickOnce

À compter de Visual Studio 2019 version 16,8, vous pouvez utiliser l’outil de **publication** pour publier des applications de bureau Windows .net Core 3,1, ou une version plus récente, à l’aide de ClickOnce à partir de Visual Studio.

> [!NOTE]
> Si vous devez publier une application Windows .NET Framework, consultez [déployer une application de bureau à l’aide de ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# ou Visual Basic).

## <a name="publishing-with-clickonce"></a>Publication avec ClickOnce

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier** (ou utilisez l’élément de menu **Générer** > **Publier**).

    ![Commande publier dans le menu contextuel du projet dans Explorateur de solutions](../deployment/media/quickstart-clickonce-solution-explorer.png "Choisir Publier")

1. Si vous avez déjà configuré des profils de publication, la page **publier** s’affiche. Sélectionnez **Nouveau**.

1. Dans l’Assistant **publication** , sélectionnez **dossier**.

    ![Choisir un dossier en tant que cible de publication](../deployment/media/quickstart-clickonce-publish-folder-category.png "Choisir un dossier")

1. Dans la page **cible spécifique** , sélectionnez **ClickOnce**.

    ![Sélectionner ClickOnce comme cible spécifique](../deployment/media/quickstart-clickonce-publish-folder-target.png "Choisir ClickOnce")

1. Entrez un chemin d’accès ou sélectionnez **Parcourir** pour sélectionner l’emplacement de publication.

    ![Spécifier le chemin d’accès de l’emplacement de publication](../deployment/media/quickstart-clickonce-publish-location.png "Entrez un chemin d’accès")

1. Dans la page **emplacement d’installation** , sélectionnez l’emplacement à partir duquel les utilisateurs installeront l’application.

    ![Spécifier le chemin d’accès au dossier](../deployment/media/quickstart-clickonce-install-location.png "Choisir l’emplacement d’installation")

1. Dans la page **paramètres** , vous pouvez fournir les paramètres nécessaires pour ClickOnce.

1. Si vous avez choisi d’installer à partir d’un chemin UNC ou d’un site Web, cette page vous permet de spécifier si l’application est disponible hors connexion. Lorsqu’elle est sélectionnée, cette option affiche l’application dans le menu Démarrer de l’utilisateur et elle permet à l’application d’être mise à jour automatiquement lorsqu’une nouvelle version est publiée. Par défaut, les mises à jour sont disponibles à partir de l’emplacement d’installation.  Si vous souhaitez disposer d’un emplacement différent pour les mises à jour, vous pouvez spécifier cette valeur à l’aide du lien paramètres de mise à jour. Si vous ne souhaitez pas que l’application soit disponible hors connexion, elle est exécutée à partir de l’emplacement d’installation.

    ![Spécifier les paramètres de publication](../deployment/media/quickstart-clickonce-unc-settings.png "Choisir les paramètres de publication")

1. Si vous avez choisi d’installer à partir d’un CD, d’un DVD ou d’un lecteur USB, cette page vous permet également de spécifier si l’application prend en charge les mises à jour automatiques. Si vous choisissez de prendre en charge les mises à jour, l’emplacement de mise à jour est obligatoire et doit être un chemin UNC ou un site Web valide.

    ![Choisir les paramètres de publication](../deployment/media/quickstart-clickonce-settings.png "Choisir les paramètres de publication")

Cette page vous permet de spécifier les **fichiers d’application** à inclure dans le programme d’installation, les packages **requis** pour l’installation et d’autres **options** via les liens en haut de la page.

Dans cette page, vous pouvez également définir la version de publication et, si la version est incrémentée automatiquement avec chaque publication.

> [!NOTE]
> Le numéro de version de publication est unique pour chaque profil ClickOnce. Si vous prévoyez d’avoir plus d’un profil, vous devrez garder cela à l’esprit.

10. Dans la page **signer les manifestes** , vous pouvez spécifier si les manifestes doivent être signés et le certificat à utiliser.

    ![Signer les manifestes ClickOnce](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. Dans la page **configuration** , vous pouvez sélectionner la configuration de projet souhaitée.

     ![Spécifier la configuration de publication](../deployment/media/quickstart-clickonce-configuration.png)

    Pour obtenir une aide supplémentaire sur le paramètre à choisir, consultez les rubriques suivantes :

    - [Déploiement dépendant du Framework et déploiement autonome](/dotnet/core/deploying/)
    - [Identificateurs du runtime cible (RID portable, et al)](/dotnet/core/rid-catalog)
    - [Configurations Debug et Release](../ide/understanding-build-configurations.md)

1. Sélectionnez **Terminer** pour enregistrer le nouveau profil de publication ClickOnce.

1. Sur la page **Résumé** , sélectionnez **publier** et Visual Studio génère le projet et le publie dans le dossier de publication spécifié. Cette page affiche également un résumé du profil.

    ![Volet de propriétés Publier affichant un récapitulatif du profil](../deployment/media/quickstart-clickonce-summary.png)

1. Pour republier, sélectionnez **Publier**.

## <a name="next-steps"></a>Étapes suivantes

Pour les applications .NET :

- [Déployer les applications .NET Framework et](/dotnet/framework/deployment/)
- [Référence ClickOnce](clickonce-reference.md)

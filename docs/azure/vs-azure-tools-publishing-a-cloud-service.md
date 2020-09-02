---
title: Publication d’un service cloud à l’aide des outils Azure | Microsoft Docs
description: Découvrez comment publier des projets de service cloud Azure à l'aide de Visual Studio.
author: ghogen
manager: jillfra
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: d8257e0833da470554ce331c30cd0edf74122093
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89313300"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Publication d'un service cloud avec Visual Studio

Visual Studio peut publier une application directement sur Azure, avec le support pour les deux environnements Intermédiaire et Production d’un service cloud. Lors de la publication, sélectionnez l’environnement de déploiement et un compte de stockage utilisé de façon temporaire pour le package de déploiement.

Lorsque vous développez et testez une application Azure, vous pouvez utiliser Web Deploy pour publier des modifications de façon incrémentielle pour vos rôles web. Une fois que vous publiez votre application dans un environnement de déploiement, Web Deploy vous permet de déployer des modifications directement sur la machine virtuelle qui exécute le rôle web. Il est inutile de créer un package et de publier votre application Azure complète chaque fois que vous souhaitez mettre à jour votre rôle web pour tester les modifications. Avec cette approche, vos modifications de rôle web sont disponibles dans le cloud et vous pouvez donc les tester sans attendre que votre application soit publiée dans un environnement de déploiement.

Utilisez les procédures suivantes pour publier votre application Azure et mettre à jour un rôle web à l'aide de Web Deploy :

- Publier ou créer un package d'une application Azure à partir de Visual Studio
- Mettre à jour un rôle web dans le cadre du cycle de test et de développement

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Publier ou créer un package d'une application Azure à partir de Visual Studio

Lorsque vous publiez votre application Azure, vous pouvez effectuer l'une des tâches suivantes :

- Créer un package de services : vous pouvez utiliser ce package et le fichier de configuration de service pour publier votre application dans un environnement de déploiement à partir du [portail Azure](https://portal.azure.com).

- Publier votre projet Azure à partir de Visual Studio : pour publier votre application directement dans Azure, vous utilisez l'Assistant Publication. Pour plus d’informations, consultez [Assistant Publication d’application Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Pour créer un package de services à partir de Visual Studio

1. Lorsque vous êtes prêt à publier votre application, ouvrez l'Explorateur de solutions, ouvrez le menu contextuel du projet Azure qui contient vos rôles, puis choisissez Publier.

1. Pour créer un package de services uniquement, procédez comme suit :

   a. Dans le menu contextuel du projet Azure, sélectionnez **Package**.

   b. Dans la boîte de dialogue **Application de package Azure**, choisissez la configuration de service pour laquelle vous souhaitez créer un package, puis la configuration de build.

   c. (facultatif) Pour activer le Bureau à distance pour le service cloud après sa publication, activez la case à cocher **Activer le Bureau à distance pour tous les rôles**, puis sélectionnez **Paramètres** pour configurer les informations d’identification le Bureau à distance. Pour plus d’informations, consultez la page [Activer la Connexion Bureau à distance pour un rôle dans Azure Cloud Services avec Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Si vous voulez déboguer votre service cloud après l'avoir publié, activez le débogage distant en sélectionnant **Activer le débogueur distant pour tous les rôles**.

   d. Pour créer le package, choisissez le lien **Package** .

      L’Explorateur de fichiers indique l'emplacement du package nouvellement créé. Vous pouvez copier cet emplacement afin de l’utiliser à partir du portail Azure.

   e. Pour publier ce package dans un environnement de déploiement, vous devez utiliser cet emplacement comme emplacement du package lorsque vous créez un service cloud et déployez ce package dans un environnement avec le portail Azure.

1. (Facultatif) Pour annuler le processus de déploiement, dans le menu contextuel de cette ligne dans le journal d'activité, choisissez **Annuler et supprimer**. Cette commande arrête le processus de déploiement et supprime l'environnement de déploiement d'Azure. Pour supprimer l’environnement après le déploiement, utilisez le portail Azure.

1. (Facultatif) Une fois vos instances de rôle démarrées, Visual Studio affiche automatiquement l’environnement de déploiement dans le nœud **Services cloud** de l’Explorateur de serveurs. Vous pouvez y voir l’état de chaque instance de rôle. Consultez [Gestion des ressources Azure avec Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md). L’illustration suivante montre les instances de rôle toujours à l’état d’initialisation :

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Mettre à jour un rôle web dans le cadre du cycle de test et de développement

Si l'infrastructure principale de votre application est stable, mais que les rôles web ont besoin d’une mise à jour plus fréquente, vous pouvez utiliser Web Deploy pour mettre à jour un seul rôle web dans votre projet. Web Deploy est pratique lorsque vous ne souhaitez pas recréer ni redéployer les rôles de travail principaux ou si vous avez plusieurs rôles web et souhaitez mettre à jour uniquement un des rôles web.

### <a name="requirements-for-using-web-deploy"></a>Configuration requise pour l’utilisation de Web Deploy

- **À des fins de développement et de test uniquement**: les modifications sont apportées directement à la machine virtuelle sur laquelle le rôle Web s’exécute. Si cette machine virtuelle doit être recyclée, les modifications sont perdues car le package d'origine que vous avez publié sert à recréer la machine virtuelle pour le rôle. Republiez votre application afin d’obtenir les dernières modifications pour le rôle web.

- **Seuls les rôles Web peuvent être mis à jour**: les rôles de travail ne peuvent pas être mis à jour. En outre, vous ne pouvez pas mettre à jour `RoleEntryPoint` dans `web role.cs`.

- **Ne peut prendre en charge qu’une seule instance d’un rôle Web**: vous ne pouvez pas avoir plusieurs instances d’un rôle Web dans votre environnement de déploiement. Toutefois, plusieurs rôles web, chacun avec une seule instance, sont pris en charge.

- **Activer les connexions Bureau à distance**: cette exigence permet à Web Deploy d’utiliser l’utilisateur et le mot de passe pour se connecter à la machine virtuelle afin de déployer les modifications sur le serveur qui exécute Internet Information Services (IIS). En outre, vous devrez peut-être vous connecter à la machine virtuelle pour ajouter un certificat approuvé à IIS sur cette machine virtuelle. (Ce certificat assure la sécurité de la connexion à distance pour IIS utilisée par Web Deploy.)

La procédure suivante suppose que vous utilisiez l’Assistant **Application de publication Azure**.

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Activez Web Deploy lorsque vous publiez votre application

1. Afin d’activer l’option **Activer Web Deploy** pour tous les rôles web, vous devez d'abord configurer les connexions Bureau à distance. Sélectionnez **Activer le Bureau à distance** pour tous les rôles, puis fournissez les informations d’identification qui seront utilisées pour se connecter à distance dans le champ **Configuration Bureau à distance** qui s’affiche. Consultez [Activer une connexion Bureau à distance pour un rôle dans Azure Cloud Services avec PowerShell](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Pour activer Web Deploy pour tous les rôles Web dans votre application, sélectionnez **Activer Web Deploy pour tous les rôles Web**.

    Un triangle d'avertissement jaune s'affiche. Web Deploy utilise par défaut un certificat non fiable et auto-signé, ce qui n'est pas recommandé pour télécharger des données sensibles. Si vous devez sécuriser ce processus pour des données sensibles, vous pouvez ajouter un certificat SSL à utiliser pour les connexions Web Deploy. Ce certificat doit être un certificat approuvé. Pour plus d’informations, consultez [Sécuriser Web Deploy](#make-web-deploy-secure).

1. Choisissez **Suivant** pour afficher l’écran **Résumé**, puis **Publier** pour déployer le service cloud.

    Le service cloud est publié. La machine virtuelle créée comporte des connexions à distance activées pour IIS, de sorte que Web Deploy peut être utilisé pour mettre à jour vos rôles web sans les republier.

   > [!NOTE]
   > Si vous avez plusieurs instances configurées pour un rôle web, un message d'avertissement s'affiche, indiquant que chaque rôle web est limité à une seule instance dans le package créé pour publier votre application. Sélectionnez **OK** pour continuer. Comme indiqué dans la section Configuration requise, vous pouvez avoir plusieurs rôles web, mais une seule instance de chaque rôle.

### <a name="update-your-web-role-by-using-web-deploy"></a>Mettre à jour votre rôle web à l'aide de Web Deploy

1. Pour utiliser Web Deploy, dans Visual Studio, modifiez le code du projet pour chaque rôle web que vous souhaitez publier, puis cliquez avec le bouton droit sur le nœud de ce projet et pointez sur **Publier**. La boîte de dialogue **Publier le site web** s'affiche.

1. (Facultatif) Si vous avez ajouté un certificat SSL approuvé à utiliser pour les connexions distantes pour IIS, vous pouvez désactiver la case à cocher **Autoriser les certificats non approuvés**. Pour plus d’informations sur l’ajout d’un certificat afin de sécuriser Web Deploy, consultez la section **Pour sécuriser Web Deploy** plus loin dans cet article.

1. Pour utiliser Web Deploy, le mécanisme de publication a besoin du nom d'utilisateur et du mot de passe que vous définissez pour votre connexion Bureau à distance lors de la publication initiale du package.

   a. Dans **Nom d’utilisateur**, entrez le nom d’utilisateur.

   b. Dans **Mot de passe**, entrez le mot de passe.

   c. (Facultatif) Si vous souhaitez enregistrer ce mot de passe de ce profil, choisissez **Enregistrer le mot de passe**.

1. Pour publier les modifications apportées à votre rôle web, choisissez **Publier**.

    La ligne d'état affiche **Démarrage de la publication**. Une fois la publication terminée, un message indique que la **publication a réussi** . Les modifications ont maintenant été déployées sur le rôle web de votre machine virtuelle. Vous pouvez désormais démarrer votre application Azure dans l'environnement Azure pour tester vos modifications.

### <a name="make-web-deploy-secure"></a>Sécuriser Web Deploy

1. Web Deploy utilise par défaut un certificat non fiable et auto-signé, ce qui n'est pas recommandé pour télécharger des données sensibles. Si vous devez sécuriser ce processus pour des données sensibles, vous pouvez ajouter un certificat SSL à utiliser pour les connexions Web Deploy. Ce certificat doit être un certificat approuvé, que vous obtenez auprès d'une autorité de certification (CA).

    Afin de sécuriser Web Deploy pour chaque machine virtuelle et chacun de vos rôles web, vous devez télécharger le certificat de confiance que vous souhaitez utiliser pour le déploiement web vers le portail Azure. Cela permet de s'assurer que le certificat est ajouté à la machine virtuelle créée pour le rôle web lorsque vous publiez votre application.

1. Pour ajouter un certificat SSL approuvé à IIS afin d'utiliser des connexions à distance, procédez comme suit :

   a. Pour vous connecter à la machine virtuelle qui exécute le rôle web, sélectionnez l’instance du rôle web dans **Cloud Explorer** ou l’**Explorateur de serveurs**, puis choisissez la commande **Connexion à l’aide de Bureau à distance**. Pour plus de détails sur les étapes de connexion à la machine virtuelle, consultez [Activer une connexion Bureau à distance pour un rôle dans Azure Cloud Services avec PowerShell](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). Votre navigateur vous invite à télécharger un `.rdp` fichier.

   b. Pour ajouter un certificat SSL, ouvrez le service de gestion dans le Gestionnaire des services IIS. Dans IIS Manager, activez SSL en ouvrant le lien **Liaisons** dans le volet **Action**. La boîte de dialogue **Ajouter la liaison de Site** s'affiche. Choisissez **Ajouter**, puis sélectionnez HTTPS dans la liste déroulante **Type**. Dans la liste **Certificat SSL**, sélectionnez le certificat SSL signé par une autorité de certification et que vous avez téléchargé sur le portail Azure. Pour plus d'informations, consultez [Configurer des paramètres de connexion pour le service de gestion](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10)).

      > [!NOTE]
      > Si vous ajoutez un certificat SSL approuvé, le triangle d'avertissement jaune ne s'affiche plus dans l'**Assistant Publication**.

## <a name="include-files-in-the-service-package"></a>Inclure des fichiers dans le package de services

Vous devrez peut-être inclure des fichiers spécifiques dans votre package de services afin qu'ils soient disponibles sur la machine virtuelle créée pour un rôle. Par exemple, vous pouvez ajouter à votre package de services un fichier `.exe` ou `.msi` utilisé par un script de démarrage. Ou vous devrez peut-être ajouter un assembly nécessaire à un projet de rôle web ou de travail. Pour inclure des fichiers, vous devez les ajouter à la solution pour votre application Azure.

1. Pour ajouter un assembly à un package de services, procédez comme suit :

   a. Dans **l'Explorateur de solutions**, ouvrez le nœud de projet pour le projet auquel il manque l'assembly référencé.
   b. Pour ajouter l'assembly au projet, ouvrez le menu contextuel du dossier **Références** et sélectionnez **Ajouter une référence**. La boîte de dialogue Ajouter une référence s'affiche.
   c. Choisissez la référence que vous souhaitez ajouter, puis sélectionnez **OK**. La référence est ajoutée à la liste sous le dossier **Références**.
   d. Ouvrez le menu contextuel de l'assembly que vous venez d'ajouter et sélectionnez **Propriétés**. La fenêtre **Propriétés** s'affiche.

      Pour inclure cet assembly dans le package de services, dans la **liste copie locale** , choisissez **true**.
1. Dans l'**Explorateur de solutions**, ouvrez le nœud de projet auquel manque l'assembly référencé.

1. Pour ajouter l'assembly au projet, ouvrez le menu contextuel du dossier **Références** et sélectionnez **Ajouter une référence**. La boîte de dialogue **Ajouter une référence** s’affiche.

1. Sélectionnez la référence à ajouter, puis cliquez sur le bouton **OK**.

    La référence est ajoutée à la liste sous le dossier **Références**.

1. Ouvrez le menu contextuel de l'assembly que vous venez d'ajouter et sélectionnez **Propriétés**. La fenêtre Propriétés apparaît.

1. Pour inclure cet assembly dans le package de services, dans la **liste de copie locale**, choisissez **True**.

1. Pour inclure des fichiers dans le package de service ajouté à votre projet de rôle web, ouvrez le menu contextuel du fichier, puis sélectionnez **Propriétés**. Dans la fenêtre **Propriétés**, sélectionnez **Contenu** dans la zone de liste **Action de génération**.

1. Pour inclure des fichiers dans le package de service ajouté à votre projet de rôle de travail, ouvrez le menu contextuel du fichier, puis sélectionnez **Propriétés**. Dans la fenêtre **Propriétés**, sélectionnez **Copier si plus récent** dans la zone de liste **Copier dans le répertoire de sortie**.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur la publication sur Azure depuis Visual Studio, consultez [Assistant Publication d’application Azure](vs-azure-tools-publish-azure-application-wizard.md).

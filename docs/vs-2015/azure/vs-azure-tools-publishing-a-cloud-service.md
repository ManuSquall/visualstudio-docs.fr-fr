---
title: Publication d’un Service Cloud à l’aide de Windows Azure Tools | Microsoft Docs
description: Découvrez comment publier des projets de service cloud Azure à l’aide de Visual Studio.
author: ghogen
manager: douge
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: cf29e1cdde71d2e8ef7caa9bc91bc31c30c7bc41
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001958"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Publication d’un service cloud avec Visual Studio

Visual Studio peut publier une application directement sur Azure, avec prise en charge pour les environnements intermédiaire et de Production d’un service cloud. Lors de la publication, vous sélectionnez l’environnement de déploiement et d’un compte de stockage qui est utilisé de façon temporaire pour le package de déploiement.

Lorsque vous développez et testez une application Azure, vous pouvez utiliser Web Deploy pour publier des modifications de façon incrémentielle pour vos rôles web. Une fois que vous publiez votre application dans un environnement de déploiement, Web Deploy vous permet de déployer les modifications directement sur l’ordinateur virtuel qui exécute le rôle web. Vous n’avez pas à empaqueter et publier votre application Azure complète chaque fois que vous souhaitez mettre à jour de votre rôle web pour tester les modifications. Avec cette approche, vous pouvez avoir vos modifications de rôle web disponibles dans le cloud pour tester sans attendre que votre application soit publiée dans un environnement de déploiement.

Utilisez les procédures suivantes pour publier votre application Azure et mettre à jour d’un rôle web à l’aide de Web Deploy :

- Publier ou empaqueter une application Azure à partir de Visual Studio
- Mettre à jour un rôle web dans le cadre du cycle de test et développement

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Publier ou empaqueter une application Azure à partir de Visual Studio

Lorsque vous publiez votre application Windows Azure, vous pouvez effectuer l’une des tâches suivantes :

- Créer un package de service : vous pouvez utiliser ce package et le fichier de configuration de service pour publier votre application dans un environnement de déploiement à partir de la [Azure portal](https://portal.azure.com).

- Publier votre projet Azure à partir de Visual Studio : pour publier votre application directement sur Azure, vous utilisez l’Assistant Publication. Pour plus d’informations, consultez [Assistant Publication d’Application Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Pour créer un package de service à partir de Visual Studio

1. Lorsque vous êtes prêt à publier votre application, ouvrez l’Explorateur de solutions, ouvrez le menu contextuel du projet Azure qui contient vos rôles et choisissez Publier.

1. Pour créer un package de service uniquement, procédez comme suit :

   a. Dans le menu contextuel du projet Azure, choisissez **Package**.

   b. Dans le **Package d’Application Azure** boîte de dialogue, choisissez la configuration du service pour lequel vous souhaitez créer un package, puis la configuration de build.

   c. (Facultatif) Pour activer le Bureau à distance pour le service cloud après sa publication, sélectionnez **activer le Bureau à distance pour tous les rôles**, puis sélectionnez **paramètres** pour configurer les informations d’identification du Bureau à distance. Pour plus d’informations, consultez [activer une connexion Bureau à distance pour un rôle dans Azure Cloud Services à l’aide de Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Si vous souhaitez déboguer votre service cloud après sa publication, activer le débogage à distance en sélectionnant **activer le débogueur distant pour tous les rôles**.

   d. Pour créer le package, choisissez le **Package** lien.

      Explorateur de fichiers indique l’emplacement du fichier du package nouvellement créé. Vous pouvez copier cet emplacement afin que vous puissiez l’utiliser à partir du portail Azure.

   e. Pour publier ce package dans un environnement de déploiement, vous devez utiliser cet emplacement comme emplacement du Package lorsque vous créez un service cloud et que vous déployez ce package dans un environnement avec le portail Azure.

1. (Facultatif) Pour annuler le processus de déploiement, dans le menu contextuel pour l’élément de ligne dans le journal d’activité, choisissez **Annuler et supprimer**. Cette commande arrête le processus de déploiement et supprime l’environnement de déploiement d’Azure. Pour supprimer l’environnement après le déploiement, utilisez le portail Azure.

1. (Facultatif) Après avoir démarré vos instances de rôle, Visual Studio affiche automatiquement l’environnement de déploiement dans le **Services Cloud** nœud dans l’Explorateur de serveurs. À ce stade, vous pouvez voir l’état de chaque instance de rôle. Consultez [gestion des ressources Azure avec Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md). L’illustration suivante montre les instances de rôle pendant qu’elles sont toujours dans l’état d’initialisation :

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Mettre à jour un rôle web dans le cadre du cycle de test et développement

Si l’infrastructure de serveur principal de votre application est stable, mais les rôles web doivent souvent plus de mises à jour, vous pouvez utiliser Web Deploy pour mettre à jour un seul rôle web dans votre projet. Web Deploy est pratique lorsque vous ne souhaitez pas recréer et redéployer les rôles de travail de serveur principal, ou si vous avez plusieurs rôles web et que vous souhaitez mettre à jour uniquement un des rôles web.

### <a name="requirements-for-using-web-deploy"></a>Configuration requise pour utiliser Web Deploy

- **Pour le développement et test qu’aux fins**: les modifications sont apportées directement à la machine virtuelle où le rôle web est en cours d’exécution. Si cet ordinateur virtuel doit être recyclé, les modifications sont perdues, car le package d’origine que vous avez publiée est utilisé pour recréer la machine virtuelle pour le rôle. Republiez votre application pour obtenir les dernières modifications pour le rôle web.

- **Seuls les rôles web peuvent être mis à jour**: rôles de travail ne peut pas être mis à jour. En outre, vous ne pouvez pas mettre à jour le `RoleEntryPoint` dans `web role.cs`.

- **Peut prendre uniquement en charge une seule instance d’un rôle web**: vous ne pouvez avoir plusieurs instances d’un rôle web dans votre environnement de déploiement. Toutefois, plusieurs rôles web chaque avec une seule instance sont prises en charge.

- **Activer les connexions Bureau à distance**: cette exigence permet que Web Deploy utilise l’utilisateur et le mot de passe pour se connecter à la machine virtuelle pour déployer les modifications sur le serveur qui exécute Internet Information Services (IIS). En outre, vous devrez peut-être vous connecter à la machine virtuelle pour ajouter un certificat approuvé à IIS sur cet ordinateur virtuel. (Ce certificat permet de s’assurer que la connexion à distance pour IIS qui est utilisé par Web Deploy est sécurisée.)

La procédure suivante suppose que vous utilisez le **publier l’Application Azure** Assistant.

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Activer Web Deploy lorsque vous publiez votre application

1. Pour activer la **activer Web Deploy pour tous les rôles web** option, vous devez d’abord configurer les connexions Bureau à distance. Sélectionnez **activer le Bureau à distance** pour tous les rôles, puis fournissez les informations d’identification qui est utilisé pour se connecter à distance dans le **Configuration Bureau à distance** boîte qui s’affiche. Consultez [activer une connexion Bureau à distance pour un rôle dans Azure Cloud Services à l’aide de Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Pour activer Web Deploy pour tous les rôles web dans votre application, sélectionnez **activer Web Deploy pour tous les rôles web**.

    Un triangle d’avertissement jaune s’affiche. Web Deploy utilise un certificat non fiable et auto-signé par défaut, ce qui n’est pas recommandé pour le chargement des données sensibles. Si vous devez sécuriser ce processus pour les données sensibles, vous pouvez ajouter un certificat SSL doit être utilisé pour les connexions Web Deploy. Ce certificat doit être un certificat approuvé. Pour plus d’informations, consultez [sécuriser web deploy](#make-web-deploy-secure).

1. Choisissez **suivant** pour afficher le **Résumé** écran, puis choisissez **publier** pour déployer le service cloud.

    Le service cloud est publié. La machine virtuelle qui est créée a des connexions distantes activées pour IIS afin que Web Deploy peut être utilisé pour mettre à jour vos rôles web sans les republier.

   > [!NOTE]
   > Si vous avez plusieurs instances configurées pour un rôle web, un message d’avertissement s’affiche, indiquant que chaque rôle web est limitée à une seule instance dans le package est créé pour publier votre application. Sélectionnez **OK** pour continuer. Comme indiqué dans la section Configuration requise, vous pouvez avoir plusieurs rôles web, mais qu’une seule instance de chaque rôle.

### <a name="update-your-web-role-by-using-web-deploy"></a>Mettre à jour votre rôle web à l’aide de Web Deploy

1. Pour utiliser Web Deploy, apporter des modifications de code au projet pour une de vos rôles web dans Visual Studio que vous souhaitez publier, puis cliquez sur ce nœud de projet dans votre solution et pointez sur **publier**. Le **publier le site Web** boîte de dialogue s’affiche.

1. (Facultatif) Si vous avez ajouté un certificat SSL approuvé à utiliser pour les connexions à distance pour IIS, vous pouvez effacer le **autoriser les certificats non approuvés** case à cocher. Pour plus d’informations sur l’ajout d’un certificat pour sécuriser Web Deploy, consultez la section **pour sécuriser Web Deploy** plus loin dans cet article.

1. Pour utiliser Web Deploy, le mécanisme de publication a besoin du nom d’utilisateur et le mot de passe que vous avez configurés pour votre connexion Bureau à distance quand vous avez publié tout d’abord le package.

   a. Dans **nom d’utilisateur**, entrez le nom d’utilisateur.

   b. Dans **mot de passe**, entrez le mot de passe.

   c. (Facultatif) Si vous souhaitez enregistrer ce mot de passe dans ce profil, choisissez **enregistrer le mot de passe**.

1. Pour publier les modifications apportées à votre rôle web, choisissez **publier**.

    Affiche la ligne d’état **publication a démarré**. Une fois la publication terminée, **publication a réussi** s’affiche. Les modifications ont maintenant été déployées sur le rôle web sur votre machine virtuelle. Vous pouvez maintenant démarrer votre application Azure dans l’environnement Azure pour tester vos modifications.

### <a name="make-web-deploy-secure"></a>Sécuriser web deploy

1. Web Deploy utilise un certificat non fiable et auto-signé par défaut, ce qui n’est pas recommandé pour le chargement des données sensibles. Si vous devez sécuriser ce processus pour les données sensibles, vous pouvez ajouter un certificat SSL doit être utilisé pour les connexions Web Deploy. Ce certificat doit être un certificat approuvé, vous obtenez à partir d’une autorité de certification (CA).

    Pour sécuriser Web Deploy pour chaque machine virtuelle pour chacun de vos rôles web, vous devez télécharger le certificat approuvé que vous souhaitez utiliser pour le web déployer sur le portail Azure. Ce certificat permet de s’assurer que le certificat est ajouté à la machine virtuelle qui est créée pour le rôle web lorsque vous publiez votre application.

1. Pour ajouter un certificat SSL approuvé à IIS à utiliser pour les connexions à distance, procédez comme suit :

   a. Pour vous connecter à la machine virtuelle qui exécute le rôle web, sélectionnez l’instance de rôle web dans **Cloud Explorer** ou **Explorateur de serveurs**, puis choisissez le **se connecter à l’aide du Bureau à distance**  commande. Pour obtenir des instructions détaillées sur la connexion à la machine virtuelle, consultez [activer une connexion Bureau à distance pour un rôle dans Azure Cloud Services à l’aide de Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). Votre navigateur vous invite à télécharger un `.rdp` fichier.

   b. Pour ajouter un certificat SSL, ouvrez le service de gestion dans le Gestionnaire des services Internet. Dans le Gestionnaire des services Internet, activez SSL en ouvrant le **liaisons** lien dans le **Action** volet. Le **ajouter la liaison de Site** boîte de dialogue s’affiche. Choisissez **ajouter**, puis sélectionnez HTTPS dans le **Type** liste déroulante. Dans le **certificat SSL** , choisissez le certificat SSL que vous aviez signé par une autorité de certification et que vous avez téléchargé vers le portail Azure. Pour plus d’informations, consultez [configurer les paramètres de connexion pour le Service de gestion](http://go.microsoft.com/fwlink/?LinkId=215824).

      > [!NOTE]
      > Si vous ajoutez un certificat SSL approuvé, le triangle d’avertissement jaune n’apparaît plus dans le **Assistant Publication**.

## <a name="include-files-in-the-service-package"></a>Inclure des fichiers dans le package de service

Vous devrez peut-être inclure des fichiers spécifiques dans votre package de service afin qu’ils soient disponibles sur l’ordinateur virtuel qui est créé pour un rôle. Par exemple, vous souhaiterez peut-être ajouter un `.exe` ou un `.msi` fichier qui est utilisé par un script de démarrage à votre package de service. Ou bien, vous devrez peut-être ajouter un assembly qui nécessite un projet de rôle web ou de travail. Pour inclure des fichiers, ils doivent être ajoutés à la solution pour votre application Windows Azure.

1. Pour ajouter un assembly à un package de service, procédez comme suit :

   a. Dans **l’Explorateur de solutions**, ouvrez le nœud de projet pour le projet auquel il manque l’assembly référencé.
   b. Pour ajouter l’assembly au projet, ouvrez le menu contextuel pour le **références** dossier, puis choisissez **ajouter une référence**. La boîte de dialogue Ajouter une référence s’affiche.
   c. Choisissez la référence que vous souhaitez ajouter, puis sélectionnez **OK**. La référence est ajoutée à la liste sous le **références** dossier.
   d. Ouvrez le menu contextuel pour l’assembly que vous avez ajouté et choisissez **propriétés**. Le **propriétés** fenêtre s’affiche.

      Pour inclure cet assembly dans le package de service, dans le **liste copie locale** choisissez **True**.
1. Dans **l’Explorateur de solutions** ouvrez le nœud de projet pour le projet auquel il manque l’assembly référencé.

1. Pour ajouter l’assembly au projet, ouvrez le menu contextuel pour le **références** dossier, puis choisissez **ajouter une référence**. Le **ajouter une référence** boîte de dialogue apparaît.

1. Choisissez la référence que vous souhaitez ajouter, puis sélectionnez le **OK** bouton.

    La référence est ajoutée à la liste sous le **références** dossier.

1. Ouvrez le menu contextuel pour l’assembly que vous avez ajouté et choisissez **propriétés**. La fenêtre Propriétés apparaît.

1. Pour inclure cet assembly dans le package de service, dans le **copie locale** , choisissez **True**.

1. Pour inclure des fichiers dans le package de service qui ont été ajoutés à votre projet de rôle web, ouvrez le menu contextuel pour le fichier, puis choisissez **propriétés**. À partir de la **propriétés** fenêtre, choisissez **contenu** à partir de la **Action de génération** zone de liste.

1. Pour inclure des fichiers dans le package de service qui ont été ajoutés à votre projet de rôle de travail, ouvrez le menu contextuel pour le fichier, puis choisissez **propriétés**. À partir de la **propriétés** fenêtre, choisissez **Copier si plus récent** à partir de la **copier dans le répertoire de sortie de** zone de liste.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur la publication vers Azure à partir de Visual Studio, consultez [Assistant Publication d’Application Azure](vs-azure-tools-publish-azure-application-wizard.md).

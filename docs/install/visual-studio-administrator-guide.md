---
title: Guide de l’administrateur Visual Studio
titleSuffix: ''
description: En savoir plus sur le déploiement de Visual Studio dans un environnement d’entreprise.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ba41c545c2af2e0490ef0410fde7849706123940
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306707"
---
# <a name="visual-studio-administrator-guide"></a>Guide de l’administrateur Visual Studio

Dans les environnements d’entreprise, les administrateurs système déploient généralement des installations pour les utilisateurs finaux à partir d’un partage réseau ou à l’aide d’un logiciel de gestion de systèmes. Nous avons conçu le moteur d’installation de Visual Studio pour prendre en charge le déploiement d’entreprise en offrant aux administrateurs système la possibilité de créer un emplacement d’installation réseau pour préconfigurer les paramètres d’installation par défaut, déployer des clés de produit pendant le processus d’installation et gérer les mises à jour de produit après un déploiement réussi.

Ce guide de l’administrateur fournit des conseils basés sur des scénarios pour un déploiement d’entreprise dans les environnements réseau.

## <a name="before-you-begin"></a>Avant de commencer

Avant de déployer Visual Studio à l’échelle de votre organisation, vous avez quelques décisions à prendre et quelques tâches à effectuer :

::: moniker range=">=vs-2019"

* Vérifiez que chaque ordinateur cible présente la [configuration minimale requise pour l’installation](/visualstudio/releases/2019/system-requirements/).

::: moniker-end

::: moniker range="vs-2017"

* Vérifiez que chaque ordinateur cible présente la [configuration minimale requise pour l’installation](/visualstudio/productinfo/vs2017-system-requirements-vs/).

::: moniker-end

* Déterminez vos besoins de maintenance.

  Si votre entreprise a besoin de rester plus longtemps sur un ensemble de fonctionnalités, mais qu’elle souhaite quand même bénéficier de mises à jour de maintenance régulières, envisagez d’utiliser un planning de référence pour la maintenance. Pour plus d’informations, consultez la section ***options de support pour les entreprises et les clients professionnels*** de la page [cycle de vie et maintenance du produit Visual Studio](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) , ainsi que la page [mettre à jour Visual Studio sur une ligne de base de maintenance](update-servicing-baseline.md) .

* Choisissez le modèle de mise à jour.

  Où voulez-vous que les ordinateurs clients individuels obtiennent les mises à jour du produit ? En particulier, déterminez si vous souhaitez que le client récupère les mises à jour à partir d’Internet ou d’un partage local à l’ensemble de l’entreprise. Ensuite, si vous choisissez d’utiliser un partage local, décidez si chaque utilisateur doit pouvoir mettre à jour son propre client ou si vous voulez qu’un administrateur mette à jour les clients par programmation. Il est préférable que ces décisions aient été prises avant l’installation d’origine sur l’ordinateur client. Pour plus d’informations, consultez [Créer une installation réseau de Visual Studio](../install/create-a-network-installation-of-visual-studio.md).

  Il est possible de mettre à jour une disposition d’installation réseau de Visual Studio avec les dernières mises à jour de produit afin qu’elles puissent être utilisées comme point d’installation pour la dernière mise à jour de Visual Studio, ainsi que pour gérer les installations déjà déployées sur les stations de travail clientes. Pour plus d’informations, consultez [mettre à jour une installation réseau de Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  Les organisations qui utilisent des outils de déploiement d’entreprise peuvent tirer parti du fait que les mises à jour de Visual Studio sont disponibles sur le catalogue Microsoft Update et Windows Server Update Services. Pour plus d’informations, consultez [activation des mises à jour de l’administrateur](../install/enabling-administrator-updates.md) et [application des mises à jour](../install/applying-administrator-updates.md)de l’administrateur.

  Pour les ordinateurs qui ne sont pas connectés à Internet, la création d’une disposition minimale est le moyen le plus simple et le plus rapide de mettre à jour vos instances de Visual Studio hors connexion. Pour plus d’informations, consultez [mettre à jour Visual Studio à l’aide d’une disposition hors connexion minimale](update-minimal-layout.md).

::: moniker range=">=vs-2019"

* Déterminez les [charges de travail et les composants](workload-and-component-ids.md?view=vs-2019&preserve-view=true) dont a besoin votre entreprise.

* Décidez s’il convient d’utiliser un [fichier réponse](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) (qui simplifie la gestion des détails dans le fichier de script).

::: moniker-end

::: moniker range="vs-2017"

* Déterminez les [charges de travail et les composants](workload-and-component-ids.md?view=vs-2017&preserve-view=true) dont a besoin votre entreprise.

* Décidez s’il convient d’utiliser un [fichier réponse](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) (qui simplifie la gestion des détails dans le fichier de script).

::: moniker-end

* Déterminez si vous souhaitez activer la stratégie de groupe et si vous voulez configurer Visual Studio pour désactiver les commentaires du client sur les ordinateurs individuels.

::: moniker range=">=vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Étape 1 – Télécharger les fichiers du produit Visual Studio

* [Sélectionnez les charges de travail et les composants](workload-and-component-ids.md?view=vs-2019&preserve-view=true) que vous souhaitez installer.

* [Créez un partage réseau pour les fichiers du produit Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Étape 2 – Créer un script d’installation

* Créez un script d’installation qui utilise des [paramètres de ligne de commande](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) pour contrôler l’installation.

  >[!NOTE]
  > Vous pouvez simplifier les scripts à l’aide d’un [fichier réponse](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true). Veillez à créer un fichier réponse qui contient votre option d’installation par défaut.

* (Facultatif) [Appliquez une clé de produit de licence en volume](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019&preserve-view=true) dans le script d’installation de sorte que les utilisateurs n’aient pas besoin d’activer le logiciel séparément.

* (Facultatif) Mettez à jour la topologie réseau pour [contrôler à quel moment les mises à jour du produit sont délivrées aux utilisateurs finaux et d’où elles proviennent](controlling-updates-to-visual-studio-deployments.md?view=vs-2019&preserve-view=true).

* (Facultatif) Définissez les stratégies de Registre qui ont une incidence sur le déploiement de Visual Studio comme l’emplacement d’installation de certains packages partagés avec d’autres versions ou instances, l’[emplacement de la mise en cache des packages](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) ou [si les packages sont mis en cache](disable-or-move-the-package-cache.md?view=vs-2019&preserve-view=true).

* (Facultatif) Définissez la stratégie de groupe. Vous pouvez aussi [configurer Visual Studio pour désactiver les commentaires du client](../ide/visual-studio-experience-improvement-program.md) sur les ordinateurs individuels.

## <a name="step-3---deploy-updates"></a>Étape 3 : déployer des mises à jour

Utilisez la technologie de déploiement de votre choix pour exécuter votre script sur vos stations de travail de développement cibles.

* [Actualiser votre emplacement réseau avec les dernières mises à jour](update-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true) de Visual Studio en exécutant régulièrement la commande utilisée à l’étape 1 pour ajouter des composants mis à jour.

  Vous pouvez mettre à jour Visual Studio à l’aide d’un script de mise à jour. Pour ce faire, utilisez le [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) paramètre de ligne de commande.

  Vous pouvez déployer des mises à jour Visual Studio à partir du Windows Server Update Services ou du catalogue Microsoft Update avec des outils tels que System Center Configuration Manager.  Pour plus d’informations, consultez [application des mises à jour](applying-administrator-updates.md) de l’administrateur. 

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Étape 4-(facultatif) utiliser les outils Visual Studio pour vérifier l’installation

Plusieurs outils sont disponibles pour vous aider à [détecter et à gérer les instances de Visual Studio installées](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true) sur les ordinateurs clients.

## <a name="advanced-configuration"></a>Configuration avancée

Par défaut, l’installation de Visual Studio active l’inclusion de type personnalisé dans Bing recherche à partir de la liste d’erreurs F1 et des liens de code. Vous pouvez configurer Visual Studio pour désactiver le mécanisme de recherche à partir d’un type d’utilisateur personnalisé, en modifiant la valeur de la clé de Registre suivante par stratégie :

**« PutCustomTypeInBingSearch » DWORD 0**

Le Registre se trouve dans le répertoire * Software\Microsoft\VisualStudio\16.0_ {InstanceId} \ Roslyn\Internal\Diagnostics \* de votre ruche de Registre privé. Pour obtenir des instructions sur l’ouverture de la ruche du Registre, consultez [modification du Registre pour une instance de Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Étape 1 – Télécharger les fichiers du produit Visual Studio

* [Sélectionnez les charges de travail et les composants](workload-and-component-ids.md?view=vs-2017&preserve-view=true) que vous souhaitez installer.

* [Créez un partage réseau pour les fichiers du produit Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Étape 2 – Créer un script d’installation

* Créez un script d’installation qui utilise des [paramètres de ligne de commande](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) pour contrôler l’installation.

  >[!NOTE]
  > Vous pouvez simplifier les scripts à l’aide d’un [fichier réponse](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true). Veillez à créer un fichier réponse qui contient votre option d’installation par défaut.

* (Facultatif) [Appliquez une clé de produit de licence en volume](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true) dans le script d’installation de sorte que les utilisateurs n’aient pas besoin d’activer le logiciel séparément.

* (Facultatif) Mettez à jour la topologie réseau pour [contrôler à quel moment les mises à jour du produit sont délivrées aux utilisateurs finaux et d’où elles proviennent](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true).

* (Facultatif) Définissez les stratégies de Registre qui ont une incidence sur le déploiement de Visual Studio comme l’emplacement d’installation de certains packages partagés avec d’autres versions ou instances, l’[emplacement de la mise en cache des packages](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) ou [si les packages sont mis en cache](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true).

* (Facultatif) Définissez la stratégie de groupe. Vous pouvez aussi [configurer Visual Studio pour désactiver les commentaires du client](../ide/visual-studio-experience-improvement-program.md) sur les ordinateurs individuels.

## <a name="step-3---deploy-updates"></a>Étape 3 : déployer des mises à jour

Utilisez la technologie de déploiement de votre choix pour exécuter votre script sur vos stations de travail de développement cibles.

* [Actualiser votre emplacement réseau avec les dernières mises à jour](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true) de Visual Studio en exécutant régulièrement la commande utilisée à l’étape 1 pour ajouter des composants mis à jour.

  Vous pouvez mettre à jour Visual Studio à l’aide d’un script de mise à jour. Pour ce faire, utilisez le [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) paramètre de ligne de commande.

  Vous pouvez déployer des mises à jour Visual Studio à partir du Windows Server Update Services ou du catalogue Microsoft Update avec des outils tels que System Center Configuration Manager. Pour plus d’informations, consultez [application des mises à jour](applying-administrator-updates.md)de l’administrateur.

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Étape 4-(facultatif) utiliser les outils Visual Studio pour vérifier l’installation

Plusieurs outils sont disponibles pour vous aider à [détecter et à gérer les instances de Visual Studio installées](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true) sur les ordinateurs clients.

## <a name="advanced-configuration"></a>Configuration avancée

Par défaut, l’installation de Visual Studio active l’inclusion de type personnalisé dans Bing recherche à partir de la liste d’erreurs F1 et des liens de code. Vous pouvez configurer Visual Studio pour désactiver le mécanisme de recherche à partir d’un type d’utilisateur personnalisé, en modifiant la valeur de la clé de Registre suivante par stratégie :

**« PutCustomTypeInBingSearch » DWORD 0**

Le Registre se trouve dans le `Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\` Répertoire de votre ruche de Registre privé. Pour obtenir des instructions sur l’ouverture de la ruche du Registre, consultez [modification du Registre pour une instance de Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Activation des mises à jour de l’administrateur](enabling-administrator-updates.md)
* [Application des mises à jour de l’administrateur](applying-administrator-updates.md)
* [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Importer ou exporter des configurations d’installation](import-export-installation-configurations.md)
* [Archives d’installation de Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Maintenance et cycle de vie des produits Visual Studio](/visualstudio/releases/2019/servicing/)
* [Paramètres du chargement automatique synchrone](../extensibility/synchronously-autoloaded-extensions.md)

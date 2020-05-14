---
title: Guide de l’administrateur Visual Studio
titleSuffix: ''
description: En savoir plus sur le déploiement de Visual Studio dans un environnement d’entreprise.
ms.date: 03/09/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: bda9a73a7a1aabb2d288653ff4d7b20b1c40db8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79190274"
---
# <a name="visual-studio-administrator-guide"></a>Guide de l’administrateur Visual Studio

Dans les environnements d’entreprise, les administrateurs système déploient généralement les installations pour les utilisateurs finaux à partir d’un partage réseau ou à l’aide d’un logiciel de gestion de systèmes. Nous avons conçu le moteur d’installation de Visual Studio pour prendre en charge le déploiement d’entreprise en offrant aux administrateurs système la possibilité de créer un emplacement d’installation réseau pour préconfigurer les paramètres d’installation par défaut, déployer des clés de produit pendant le processus d’installation et gérer les mises à jour de produit après un déploiement réussi.

Ce guide de l’administrateur fournit des conseils basés sur des scénarios pour un déploiement d’entreprise dans les environnements réseau.

## <a name="before-you-begin"></a>Avant de commencer

Avant de déployer Visual Studio à l’échelle de votre organisation, vous avez quelques décisions à prendre et quelques tâches à effectuer :

::: moniker range="vs-2019"

* Vérifiez que chaque ordinateur cible présente la [configuration minimale requise pour l’installation](/visualstudio/releases/2019/system-requirements/).

* Déterminez vos besoins de maintenance.

  Si votre entreprise a besoin de rester plus longtemps sur un ensemble de fonctionnalités, mais qu’elle souhaite quand même bénéficier de mises à jour de maintenance régulières, envisagez d’utiliser un planning de référence pour la maintenance. Pour plus d’informations, consultez la section ***Options de support pour les clients d’entreprise et professionnels*** du cycle de vie et de [l’entretien du visual studio,](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) ainsi que la page Comment mettre à jour Visual Studio sur une page de référence des [services.](update-servicing-baseline.md)

  Si vous envisagez d’appliquer des mises à jour de maintenance parallèlement aux mises à jour cumulatives des fonctionnalités, vous pouvez choisir les derniers composants.

* Choisissez le modèle de mise à jour.

  D’où doivent provenir les mises à jour pour les machines clientes ? Concrètement, déterminez si vous voulez obtenir les mises à jour d’Internet ou d’un partage local à l’échelle de l’entreprise. Ensuite, si vous choisissez d’utiliser un partage local, décidez si chaque utilisateur doit pouvoir mettre à jour son propre client ou si vous voulez qu’un administrateur mette à jour les clients par programmation.

* Déterminez les [charges de travail et les composants](workload-and-component-ids.md?view=vs-2019) dont a besoin votre entreprise.

* Décidez s’il convient d’utiliser un [fichier réponse](automated-installation-with-response-file.md?view=vs-2019) (qui simplifie la gestion des détails dans le fichier de script).

* Déterminez si vous souhaitez activer la stratégie de groupe et si vous voulez configurer Visual Studio pour désactiver les commentaires du client sur les ordinateurs individuels.

::: moniker-end

::: moniker range="vs-2017"

* Vérifiez que chaque ordinateur cible présente la [configuration minimale requise pour l’installation](/visualstudio/productinfo/vs2017-system-requirements-vs/).

* Déterminez vos besoins de maintenance.

  Si votre entreprise a besoin de rester plus longtemps sur un ensemble de fonctionnalités, mais qu’elle souhaite quand même bénéficier de mises à jour de maintenance régulières, envisagez d’utiliser un planning de référence pour la maintenance. Pour plus d’informations, consultez le ***Support for older versions de visual Studio*** section du cycle de vie et de la page [d’entretien du produit Visual Studio,](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) ainsi que le How to: Update Visual Studio sur une page [de base d’entretien.](update-servicing-baseline.md)

  Si vous envisagez d’appliquer des mises à jour de maintenance parallèlement aux mises à jour cumulatives des fonctionnalités, vous pouvez choisir les derniers composants.

* Choisissez le modèle de mise à jour.

  D’où doivent provenir les mises à jour pour les machines clientes ? Concrètement, déterminez si vous voulez obtenir les mises à jour d’Internet ou d’un partage local à l’échelle de l’entreprise. Ensuite, si vous choisissez d’utiliser un partage local, décidez si chaque utilisateur doit pouvoir mettre à jour son propre client ou si vous voulez qu’un administrateur mette à jour les clients par programmation.

* Déterminez les [charges de travail et les composants](workload-and-component-ids.md?view=vs-2017) dont a besoin votre entreprise.

* Décidez s’il convient d’utiliser un [fichier réponse](automated-installation-with-response-file.md?view=vs-2017) (qui simplifie la gestion des détails dans le fichier de script).

* Déterminez si vous souhaitez activer la stratégie de groupe et si vous voulez configurer Visual Studio pour désactiver les commentaires du client sur les ordinateurs individuels.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Étape 1 – Télécharger les fichiers du produit Visual Studio

* [Sélectionnez les charges de travail et les composants](workload-and-component-ids.md?view=vs-2019) que vous souhaitez installer.

* [Créez un partage réseau pour les fichiers du produit Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>Étape 2 – Créer un script d’installation

* Créez un script d’installation qui utilise des [paramètres de ligne de commande](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) pour contrôler l’installation.

  >[!NOTE]
  > Vous pouvez simplifier les scripts à l’aide d’un [fichier réponse](automated-installation-with-response-file.md?view=vs-2019). Veillez à créer un fichier réponse qui contient votre option d’installation par défaut.

* (Facultatif) [Appliquez une clé de produit de licence en volume](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019) dans le script d’installation de sorte que les utilisateurs n’aient pas besoin d’activer le logiciel séparément.

* (Facultatif) Mettez à jour la topologie réseau pour [contrôler à quel moment les mises à jour du produit sont délivrées aux utilisateurs finaux et d’où elles proviennent](controlling-updates-to-visual-studio-deployments.md?view=vs-2019).

* (Facultatif) Définissez les stratégies de Registre qui ont une incidence sur le déploiement de Visual Studio comme l’emplacement d’installation de certains packages partagés avec d’autres versions ou instances, l’[emplacement de la mise en cache des packages](set-defaults-for-enterprise-deployments.md?view=vs-2019) ou [si les packages sont mis en cache](disable-or-move-the-package-cache.md?view=vs-2019).

* (Facultatif) Définissez la stratégie de groupe. Vous pouvez aussi [configurer Visual Studio pour désactiver les commentaires du client](../ide/visual-studio-experience-improvement-program.md) sur les ordinateurs individuels.

## <a name="step-3---deploy"></a>Étape 3 – Déployer

* Utilisez la technologie de déploiement de votre choix pour exécuter votre script sur vos stations de travail de développement cibles.

## <a name="step-4---deploy-updates"></a>Étape 4 – Déployer les mises à jour

* [Actualiser votre emplacement réseau avec les dernières mises à jour](update-a-network-installation-of-visual-studio.md?view=vs-2019) de Visual Studio en exécutant régulièrement la commande utilisée à l’étape 1 pour ajouter des composants mis à jour.

  Vous pouvez mettre à jour Visual Studio à l’aide d’un script de mise à jour. Pour ce faire, [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) utilisez le paramètre de la ligne de commande.

## <a name="step-5---optional-use-visual-studio-tools"></a>Étape 5 – (Facultatif) Utiliser les outils Visual Studio

Plusieurs outils sont disponibles pour vous aider à [détecter et à gérer les instances de Visual Studio installées](tools-for-managing-visual-studio-instances.md?view=vs-2019) sur les ordinateurs clients.

## <a name="advanced-configuration"></a>Configuration avancée

Par défaut, l’installation Visual Studio permet l’inclusion de type personnalisé dans les recherches Bing à partir de la liste d’erreurs F1 et des liens de code. Vous pouvez configurer Visual Studio pour désactiver le mécanisme de recherche d’inclure tous les types d’utilisateurs personnalisés en modifiant la valeur de la clé de registre suivante par la stratégie :

**"PutCustomTypeInBingSearch" DWORD 0**

Le registre est situé dans le\* répertoire de votre ruche privée. Pour obtenir des instructions sur la façon d’ouvrir la ruche du registre, voir [l’édition du registre pour une instance Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Étape 1 – Télécharger les fichiers du produit Visual Studio

* [Sélectionnez les charges de travail et les composants](workload-and-component-ids.md?view=vs-2017) que vous souhaitez installer.

* [Créez un partage réseau pour les fichiers du produit Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017).

## <a name="step-2---build-an-installation-script"></a>Étape 2 – Créer un script d’installation

* Créez un script d’installation qui utilise des [paramètres de ligne de commande](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) pour contrôler l’installation.

  >[!NOTE]
  > Vous pouvez simplifier les scripts à l’aide d’un [fichier réponse](automated-installation-with-response-file.md?view=vs-2017). Veillez à créer un fichier réponse qui contient votre option d’installation par défaut.

* (Facultatif) [Appliquez une clé de produit de licence en volume](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017) dans le script d’installation de sorte que les utilisateurs n’aient pas besoin d’activer le logiciel séparément.

* (Facultatif) Mettez à jour la topologie réseau pour [contrôler à quel moment les mises à jour du produit sont délivrées aux utilisateurs finaux et d’où elles proviennent](controlling-updates-to-visual-studio-deployments.md?view=vs-2017).

* (Facultatif) Définissez les stratégies de Registre qui ont une incidence sur le déploiement de Visual Studio comme l’emplacement d’installation de certains packages partagés avec d’autres versions ou instances, l’[emplacement de la mise en cache des packages](set-defaults-for-enterprise-deployments.md?view=vs-2019) ou [si les packages sont mis en cache](disable-or-move-the-package-cache.md?view=vs-2017).

* (Facultatif) Définissez la stratégie de groupe. Vous pouvez aussi [configurer Visual Studio pour désactiver les commentaires du client](../ide/visual-studio-experience-improvement-program.md) sur les ordinateurs individuels.

## <a name="step-3---deploy"></a>Étape 3 – Déployer

* Utilisez la technologie de déploiement de votre choix pour exécuter votre script sur vos stations de travail de développement cibles.

## <a name="step-4---deploy-updates"></a>Étape 4 – Déployer les mises à jour

* [Actualiser votre emplacement réseau avec les dernières mises à jour](update-a-network-installation-of-visual-studio.md?view=vs-2017) de Visual Studio en exécutant régulièrement la commande utilisée à l’étape 1 pour ajouter des composants mis à jour.

  Vous pouvez mettre à jour Visual Studio à l’aide d’un script de mise à jour. Pour ce faire, [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) utilisez le paramètre de la ligne de commande.

## <a name="step-5---optional-use-visual-studio-tools"></a>Étape 5 – (Facultatif) Utiliser les outils Visual Studio

Plusieurs outils sont disponibles pour vous aider à [détecter et à gérer les instances de Visual Studio installées](tools-for-managing-visual-studio-instances.md?view=vs-2017) sur les ordinateurs clients.

## <a name="advanced-configuration"></a>Configuration avancée

Par défaut, l’installation Visual Studio permet l’inclusion de type personnalisé dans les recherches Bing à partir de la liste d’erreurs F1 et des liens de code. Vous pouvez configurer Visual Studio pour désactiver le mécanisme de recherche d’inclure tous les types d’utilisateurs personnalisés en modifiant la valeur de la clé de registre suivante par la stratégie :

**"PutCustomTypeInBingSearch" DWORD 0**

Le registre est situé dans le\* répertoire de votre ruche privée. Pour obtenir des instructions sur la façon d’ouvrir la ruche du registre, voir [l’édition du registre pour une instance Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Importer ou exporter des configurations d’installation](import-export-installation-configurations.md)
* [Archives d’installation de Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Cycle de vie et entretien du produit Visual Studio](/visualstudio/releases/2019/servicing/)
* [Paramètres du chargement automatique synchrone](../extensibility/synchronously-autoloaded-extensions.md)

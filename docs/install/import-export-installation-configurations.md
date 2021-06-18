---
title: Importer ou exporter des configurations d’installation
titleSuffix: ''
description: Découvrez comment exporter la configuration de votre installation dans un fichier .vsconfig à partager avec d’autres utilisateurs et comment l’importer pour le cloner.
ms.date: 05/18/2019
ms.topic: how-to
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1fc4b181436b5e214300b334163b9257af0d0d35
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307464"
---
# <a name="import-or-export-installation-configurations"></a>Importer ou exporter des configurations d’installation

Vous pouvez configurer Visual Studio pour l’ensemble de votre organisation avec des fichiers de configuration d’installation. Pour ce faire, exportez simplement les informations sur la charge de travail et le composant dans un fichier .vsconfig en utilisant le programme d’installation de Visual Studio. Vous pouvez ensuite importer la configuration dans des installations nouvelles ou existantes et même les partager avec d’autres utilisateurs.

Voici comment procéder.

::: moniker range="vs-2017"

> [!NOTE]
> Cette fonctionnalité est uniquement disponible dans Visual Studio 2017 version 15.9 et ultérieure.

::: moniker-end

## <a name="export-a-configuration"></a>Exporter une configuration

Vous pouvez choisir d’exporter un fichier de configuration de l’installation à partir d’une instance précédemment installée de Visual Studio ou d’une instance en cours d’installation.

1. Ouvrez le programme d’installation de Visual Studio.

1. Dans la fiche produit, choisissez le bouton **Plus**, puis sélectionnez **Exporter la configuration**.

   ![Exporter la configuration à partir de la fiche produit dans le programme d’installation de Visual Studio](../install/media/vs-2019/vs-installer-export-config.png)

1. Recherchez ou tapez l’emplacement où vous voulez enregistrer votre fichier .vconfig, puis choisissez **Passer en revue les détails**.

   ![Exporter la configuration à partir du programme d’installation de Visual Studio](../install/media/vs-2019/export-configuration-confirmation.png)

1. Assurez-vous d’avoir les charges de travail et les composants que vous souhaitez, puis choisissez **Exporter**.

## <a name="import-a-configuration"></a>Importer une configuration

Lorsque vous êtes prêt à importer un fichier de configuration de l’installation, procédez comme suit.

1. Ouvrez le programme d’installation de Visual Studio.

1. Dans la fiche produit, choisissez le bouton **Plus**, puis sélectionnez **Importer la configuration**.

1. Recherchez le fichier .vconfig que vous voulez importer, puis choisissez **Passer en revue les détails**.

1. Assurez-vous d’avoir les charges de travail et les composants que vous souhaitez, puis choisissez **Fermer**.

::: moniker range=">=vs-2019"

## <a name="automatically-install-missing-components"></a>Installer automatiquement les composants manquants

**Nouveauté de Visual studio 2019**: quand vous enregistrez un fichier. vsconfig dans le répertoire racine de votre solution, puis que vous ouvrez une solution, Visual Studio détecte automatiquement les composants manquants et vous invite à les installer.

![L’Explorateur de solutions suggère des composants supplémentaires](../install/media/vs-2019/solution-explorer-config-file.png)

Vous pouvez également générer un fichier .vsconfig directement à partir de l’Explorateur de solutions.

1. Cliquez avec le bouton droit sur votre fichier de solution.

1. Choisissez **Ajouter** un > **fichier de configuration d’installation**.

1. Confirmez l’emplacement où vous souhaitez enregistrer le fichier .vsconfig, puis choisissez **Vérifier les détails**.

1. Assurez-vous d’avoir les charges de travail et les composants que vous souhaitez, puis choisissez **Exporter**.

::: moniker-end

> [!NOTE]
> Pour plus d’informations, consultez le billet de blog [Configure Visual Studio across your organization with .vsconfig](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Définir les valeurs par défaut des déploiements d’entreprise](set-defaults-for-enterprise-deployments.md)

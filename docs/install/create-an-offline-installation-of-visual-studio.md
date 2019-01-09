---
title: Créer une installation hors connexion
description: Découvrez comment installer Visual Studio hors connexion quand vous avez une connexion Internet non fiable ou une bande passante faible.
ms.date: 08/28/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8359a3b0d96c92a897532edffa7c6ac0b193cd3c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952394"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Créer une installation hors connexion de Visual Studio 2017

Nous avons conçu Visual Studio 2017 pour qu’il fonctionne correctement dans un large éventail de configurations réseau et informatiques. Bien que nous vous recommandions d’essayer le [programme d’installation web de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;qui est un petit fichier vous permettant d’être à jour des derniers correctifs et fonctionnalités&mdash;nous sommes conscients du fait que cela n’est peut-être pas possible pour vous.

Par exemple, vous avez peut-être une connexion Internet non fiable ou une bande passante faible. Dans ce cas, vous avez le choix entre plusieurs options : Vous pouvez utiliser la nouvelle fonctionnalité « Tout télécharger, puis installer » pour télécharger les fichiers avant de les installer, ou vous pouvez utiliser la ligne de commande pour créer un cache local des fichiers.

> [!NOTE]
> Si vous êtes administrateur d’entreprise et que vous souhaitez effectuer un déploiement de Visual Studio 2017 sur un réseau de stations de travail clientes qui sont protégées d’Internet par un pare-feu, consultez nos pages [Créer une installation réseau de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) et [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="use-the-download-all-then-install-feature"></a>Utiliser la fonctionnalité « Tout télécharger, puis installer »

[**Nouveautés de la version 15.8**](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017#install
) : Après avoir téléchargé le programme d’installation web, sélectionnez la nouvelle option **Tout télécharger, puis installer** à partir de Visual Studio Installer. Poursuivez ensuite l’installation.

   ![Option « Tout télécharger, puis installer »](media/download-all-then-install.png)

## <a name="use-the-command-line-to-create-a-local-cache"></a>Utiliser la ligne de commande pour créer un cache local

Après avoir téléchargé un petit programme d’amorçage, utilisez la ligne de commande pour créer un cache local. Utilisez ensuite le cache local pour installer Visual Studio. (Ce processus remplace les fichiers ISO disponibles pour les versions précédentes.)

Voici comment procéder.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Étape 1 : Télécharger le programme d’amorçage de Visual Studio

Vous devez avoir une connexion Internet pour effectuer cette étape.

Commencez par télécharger le programme d’amorçage de Visual Studio pour l’édition de Visual Studio que vous avez choisie. Votre fichier d’installation &mdash;ou programme d’amorçage&mdash; correspond ou est similaire à l’une des valeurs suivantes.

| Édition                    | Fichier                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Communauté Visual Studio    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

### <a name="step-2---create-a-local-install-cache"></a>Étape 2 : Créer un cache d’installation local

Vous devez avoir une connexion Internet pour effectuer cette étape.

> [!IMPORTANT]
> Si vous installez Visual Studio Community 2017, vous devez l’activer dans les 30 jours suivant l’installation. Une connexion Internet est requise.

Ouvrez une invite de commandes et utilisez l’une des commandes des exemples suivants. Les exemples listés ici supposent que vous utilisez l’édition Community de Visual Studio. Changez la commande en fonction de votre édition.

- Pour le développement d’applications de bureau .NET et web .NET, exécutez :

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- Pour le développement d’applications de bureau .NET et Office, exécutez :

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Pour le développement d’applications de bureau C++, exécutez :

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Pour créer une disposition locale complète avec toutes les fonctionnalités (cela prendra un certain temps &mdash; nous avons _beaucoup_ de fonctionnalités !), exécutez ceci :

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Si vous souhaitez installer une autre langue que l’anglais, remplacez `en-US` par l’un des paramètres régionaux de la [liste des paramètres régionaux de langue](#list-of-language-locales). Utilisez ensuite la [liste des composants et charges de travail disponibles](workload-and-component-ids.md) pour personnaliser davantage votre cache d’installation.

> [!IMPORTANT]
> Une disposition Visual Studio 2017 complète nécessite au moins 35 Go d’espace disque et peut être assez longue à télécharger. Pour plus d’informations sur la création d’une disposition comprenant uniquement les composants que vous souhaitez installer, consultez [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md).

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Étape 3 : Installer Visual Studio à partir du cache local

> [!TIP]
> Quand vous procédez à l’exécution à partir d’un cache d’installation local, le programme d’installation utilise les versions locales de chacun de ces fichiers. Toutefois, si durant l’installation, vous sélectionnez des composants qui ne sont pas dans le cache, le programme d’installation tente de les télécharger à partir d’Internet.

Pour vérifier que vous installez uniquement les fichiers que vous avez téléchargés, utilisez les mêmes options de ligne de commande que celles ayant servi à créer le cache de disposition. Par exemple, si vous avez créé un cache de disposition avec la commande suivante :

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Utilisez ensuite cette commande pour exécuter l’installation :

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> Si vous obtenez une erreur indiquant qu’une signature n’est pas valide, vous devez installer les certificats mis à jour. Ouvrez le dossier des certificats dans votre cache hors connexion. Double-cliquez sur chacun des fichiers de certificat, puis suivez les étapes de l’Assistant du Gestionnaire de certificats. Si un mot de passe vous est demandé, n’indiquez rien.

### <a name="list-of-language-locales"></a>Liste des paramètres régionaux de langue

| **Paramètres régionaux de langue** | **Language** |
| ----------------------- | --------------- |
| cs-CZ | Tchèque |
| de-DE | Allemand |
| en-US | Anglais |
| es-ES | Espagnol |
| fr-FR | Français |
| it-IT | Italien |
| ja-JP | Japonais |
| ko-KR | Coréen |
| pl-PL | Polonais |
| pt-BR | Portugais - Brésil |
| ru-RU | Russe |
| tr-TR | Turc |
| zh-CN | Chinois (simplifié) |
| zh-TW | Chinois (traditionnel) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

- [Créer une installation réseau de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md)
- [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [ID de charge de travail et de composant Visual Studio 2017](workload-and-component-ids.md)

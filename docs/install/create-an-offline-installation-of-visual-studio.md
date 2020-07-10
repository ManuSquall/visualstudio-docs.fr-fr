---
title: Créer une installation hors connexion
description: Découvrez comment installer Visual Studio hors connexion quand vous avez une connexion Internet non fiable ou une bande passante faible.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1c658d97ed678950869c9a011af04e04eeacf5b1
ms.sourcegitcommit: 46547f0bf3fc1a81e1a906762106dec5855e6e4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86156817"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Créer une installation hors connexion de Visual Studio

::: moniker range="vs-2017"

Nous avons conçu Visual Studio 2017 pour qu’il fonctionne correctement dans un large éventail de configurations réseau et informatiques. Nous vous recommandons d’essayer le [programme d’installation Web de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads) &mdash; , qui est un petit fichier qui vous permet de vous tenir informé de tous les correctifs et fonctionnalités les plus récents &mdash; que vous ne pourrez peut-être pas.

::: moniker-end

::: moniker range="vs-2019"

Nous avons conçu Visual Studio 2019 pour qu’il fonctionne correctement dans un large éventail de configurations réseau et informatiques. Nous vous recommandons d’essayer le [programme d’installation Web de Visual Studio](https://visualstudio.microsoft.com/downloads) &mdash; , qui est un petit fichier qui vous permet de vous tenir informé de tous les correctifs et fonctionnalités les plus récents &mdash; que vous ne pourrez peut-être pas.

::: moniker-end

Par exemple, vous avez peut-être une connexion Internet non fiable ou une bande passante faible. Dans ce cas, vous avez quelques options : vous pouvez utiliser la nouvelle fonctionnalité « Tout télécharger, puis installer » pour télécharger les fichiers avant de les installer, ou vous pouvez utiliser la ligne de commande pour créer un cache local des fichiers.

> [!NOTE]
> Si vous êtes administrateur en entreprise et que vous souhaitez effectuer un déploiement de Visual Studio sur un réseau de stations de travail clientes qui sont protégées d’Internet par un pare-feu, consultez nos pages [Créer une installation réseau de Visual Studio](../install/create-a-network-installation-of-visual-studio.md) et [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="use-the-download-all-then-install-feature"></a>Utiliser la fonctionnalité « Tout télécharger, puis installer »

::: moniker range="vs-2017"

[**Nouveauté de la version 15,8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): après avoir téléchargé le programme d’installation Web, sélectionnez l’option nouveau **Télécharger tout, puis installer** à partir du Visual Studio installer. Poursuivez ensuite l’installation.

   ![Option « Tout télécharger, puis installer »](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

Après avoir téléchargé le programme d’installation web, sélectionnez la nouvelle option **Tout télécharger, puis installer** à partir de Visual Studio Installer. Poursuivez ensuite l’installation.

   ![Option « Tout télécharger, puis installer »](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Nous avons conçu la fonctionnalité « Tout télécharger, puis installer » pour vous permettre de télécharger Visual Studio en une seule installation pour le même ordinateur que celui utilisé pour le téléchargement. De cette façon, vous pouvez en toute sécurité vous déconnecter du web avant d’installer Visual Studio.

> [!IMPORTANT]
> N’utilisez pas la fonctionnalité « Tout télécharger, puis installer » pour créer un cache hors connexion que vous souhaitez transférer vers un autre ordinateur. Cela n’est pas conçu pour fonctionner de cette façon. <br><br>Si vous souhaitez créer un cache hors connexion pour installer Visual Studio sur un autre ordinateur, consultez la section [Utiliser la ligne de commande pour créer un cache local](#use-the-command-line-to-create-a-local-cache) de cette page pour plus d’informations sur la création d’un cache local, ou la page [Créer une installation réseau de Visual Studio](../install/create-a-network-installation-of-visual-studio.md) pour plus d’informations sur la création d’un cache réseau.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Utiliser la ligne de commande pour créer un cache local

Après avoir téléchargé un petit programme d’amorçage, utilisez la ligne de commande pour créer un cache local. Utilisez ensuite le cache local pour installer Visual Studio. (Ce processus remplace les fichiers ISO disponibles pour les versions précédentes.)

Voici comment faire.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Étape 1 : Télécharger le programme d’amorçage de Visual Studio

Vous devez avoir une connexion Internet pour terminer cette étape.

::: moniker range="vs-2017"

Pour obtenir un programme d’amorçage pour Visual Studio 2017, consultez la page de téléchargement des [versions précédentes de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) pour plus d’informations sur la façon de procéder.

L’exécutable de votre programme d’installation &mdash; ou pour être plus précis, le fichier du programme d’amorçage &mdash; doit correspondre ou être similaire à l’un des éléments suivants.

| Édition | Nom de fichier |
|-------------|-----------------------|
|Communauté Visual Studio | vs_community.exe |
|Visual Studio Professional | vs_professional.exe |
|Visual Studio Enterprise | vs_enterprise.exe |
|Visual Studio Build Tools   | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Commencez par télécharger le programme d’amorçage de Visual Studio pour l’édition de Visual Studio que vous avez choisie. Votre fichier d’installation &mdash;ou programme d’amorçage&mdash; correspond ou est similaire à l’une des valeurs suivantes.

| Édition                    | Fichier                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Communauté Visual Studio    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

>[!TIP]
>Si vous avez précédemment téléchargé un fichier de programme d’amorçage et que vous souhaitez vérifier sa version, voici comment procéder. Dans Windows, ouvrez l’Explorateur de fichiers, cliquez avec le bouton droit sur le fichier du programme d’amorçage, choisissez **Propriétés**, cliquez sur l’onglet **Détails** , puis affichez le numéro de **version du produit** . Pour faire correspondre ce nombre à une version de Visual Studio, consultez la page [numéros de build et dates de publication de Visual Studio](visual-studio-build-numbers-and-release-dates.md) .

### <a name="step-2---create-a-local-install-cache"></a>Étape 2 : Créer un cache d’installation local

Vous devez avoir une connexion Internet pour terminer cette étape.

> [!IMPORTANT]
> Si vous installez Visual Studio Community, vous devez l’activer dans les 30 jours suivant l’installation. Une connexion Internet est requise.

Ouvrez une invite de commandes et utilisez l’une des commandes des exemples suivants. Les exemples listés ici supposent que vous utilisez l’édition Community de Visual Studio. Changez la commande en fonction de votre édition.

> [!TIP]
> Pour éviter toute erreur, vérifiez que votre chemin d’installation complet fait moins de 80 caractères.

- Pour le développement d’applications de bureau .NET et web .NET, exécutez :

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Pour le développement d’applications de bureau .NET et Office, exécutez :

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Pour le développement d’applications de bureau C++, exécutez :

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Pour créer une disposition locale complète avec toutes les fonctionnalités (cela prendra un certain temps &mdash; nous avons _beaucoup_ de fonctionnalités !), exécutez ceci :

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Une disposition Visual Studio complète nécessite un minimum de 35 Go d’espace disque. Pour plus d’informations, consultez [Configuration système requise](/visualstudio/productinfo/vs2017-system-requirements-vs/). Pour plus d’informations sur la façon de créer une disposition comprenant seulement les composants que vous souhaitez installer, consultez [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Une disposition Visual Studio complète nécessite un minimum de 35 Go d’espace disque. Pour plus d’informations, consultez [Configuration système requise](/visualstudio/releases/2019/system-requirements/). Pour plus d’informations sur la façon de créer une disposition comprenant seulement les composants que vous souhaitez installer, consultez [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

Si vous souhaitez installer une autre langue que l’anglais, remplacez `en-US` par l’un des paramètres régionaux de la [liste des paramètres régionaux de langue](#list-of-language-locales). Utilisez ensuite la [liste des composants et charges de travail disponibles](workload-and-component-ids.md) pour personnaliser davantage votre cache d’installation.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Étape 3 : Installer Visual Studio à partir du cache local

> [!TIP]
> Quand vous procédez à l’exécution à partir d’un cache d’installation local, le programme d’installation utilise les versions locales de chacun de ces fichiers. Toutefois, si durant l’installation, vous sélectionnez des composants qui ne sont pas dans le cache, le programme d’installation tente de les télécharger à partir d’Internet.

::: moniker range="vs-2019"
> [!IMPORTANT]
> Pour les installations hors connexion, si vous recevez un message d’erreur indiquant « un produit correspondant aux paramètres suivants est introuvable », vérifiez que vous utilisez le `--noweb` commutateur avec la version 16.3.5 ou ultérieure.
>
::: moniker-end

Pour vérifier que vous installez uniquement les fichiers que vous avez téléchargés, utilisez les mêmes options de ligne de commande que celles ayant servi à créer le cache de disposition. Par exemple, si vous avez créé un cache de disposition avec la commande suivante :

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Utilisez ensuite cette commande pour exécuter l’installation :

```cmd
c:\vslayout\vs_community.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

Pour obtenir plus d’exemples d’utilisation des [paramètres de ligne de commande](use-command-line-parameters-to-install-visual-studio.md), consultez la page d’installation des [exemples de paramètres de ligne de commande pour Visual Studio](command-line-parameter-examples.md) . 

> [!NOTE]
> Si vous obtenez une erreur indiquant qu’une signature n’est pas valide, vous devez installer les certificats mis à jour. Ouvrez le dossier des certificats dans votre cache hors connexion. Double-cliquez sur chacun des fichiers de certificat, puis suivez les étapes de l’Assistant du Gestionnaire de certificats. Si un mot de passe vous est demandé, n’indiquez rien.

### <a name="list-of-language-locales"></a>Liste des paramètres régionaux de langue

| **Paramètres régionaux de langue** | **Langage** |
| ----------------------- | --------------- |
| cs-CZ | Tchèque |
| de-DE | Allemand |
| fr-FR | Anglais |
| es-ES | Espagnol |
| fr-FR | Français |
| it-IT | Italien |
| ja-JP | Japonais |
| ko-KR | Coréen |
| pl-PL | Polonais |
| pt-br | Portugais - Brésil |
| ru-RU | Russe |
| tr-TR | Turc |
| zh-CN | Chinois - simplifié |
| zh-TW | Chinois - traditionnel |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

- [Créer une installation réseau de Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)

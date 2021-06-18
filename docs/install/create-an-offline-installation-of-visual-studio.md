---
title: Créer une installation hors connexion
description: Découvrez comment installer Visual Studio hors connexion quand vous avez une connexion Internet non fiable ou une bande passante faible.
ms.date: 4/16/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: eef6a8bbdf5afc3aa5f36b0afdb374fd5beac471
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307490"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Créer une installation hors connexion de Visual Studio

::: moniker range="vs-2017"

Nous avons conçu Visual Studio 2017 pour qu’il fonctionne correctement dans un large éventail de configurations réseau et informatiques. Nous vous recommandons d’essayer le [programme d’installation Web de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads), qui &mdash; est un petit fichier qui vous permet de vous tenir informé de tous les correctifs et fonctionnalités les plus récents que &mdash; vous ne pourrez peut-être pas.

::: moniker-end

::: moniker range=">=vs-2019"

Nous avons conçu Visual Studio 2019 et versions ultérieures pour fonctionner correctement dans de nombreuses configurations réseau et ordinateur. Nous vous recommandons d’essayer le [programme d’installation Web de Visual Studio](https://visualstudio.microsoft.com/downloads), qui &mdash; est un petit fichier qui vous permet de vous tenir informé de tous les correctifs et fonctionnalités les plus récents que &mdash; vous ne pourrez peut-être pas.

::: moniker-end

Par exemple, vous avez peut-être une connexion Internet non fiable ou une bande passante faible. Dans ce cas, vous avez quelques options : vous pouvez utiliser la nouvelle fonctionnalité « Tout télécharger, puis installer » pour télécharger les fichiers avant de les installer, ou vous pouvez utiliser la ligne de commande pour créer un cache local des fichiers.

> [!NOTE]
> Si vous êtes administrateur en entreprise et que vous souhaitez effectuer un déploiement de Visual Studio sur un réseau de stations de travail clientes qui sont protégées d’Internet par un pare-feu, consultez nos pages [Créer une installation réseau de Visual Studio](../install/create-a-network-installation-of-visual-studio.md) et [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="use-the-download-all-then-install-feature"></a>Utiliser la fonctionnalité « Tout télécharger, puis installer »

::: moniker range="vs-2017"

[**Nouveauté de la version 15,8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): après avoir téléchargé le programme d’installation Web, sélectionnez l’option nouveau **Télécharger tout, puis installer** à partir du Visual Studio installer. Poursuivez ensuite l’installation.

   ![Option « Tout télécharger, puis installer »](media/download-all-then-install.png)

::: moniker-end

::: moniker range=">=vs-2019"

Après avoir téléchargé le programme d’installation web, sélectionnez la nouvelle option **Tout télécharger, puis installer** à partir de Visual Studio Installer. Poursuivez ensuite l’installation.

   ![Option « Tout télécharger, puis installer »](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Nous avons conçu la fonctionnalité « Tout télécharger, puis installer » pour vous permettre de télécharger Visual Studio en une seule installation pour le même ordinateur que celui utilisé pour le téléchargement. De cette façon, vous pouvez en toute sécurité vous déconnecter du web avant d’installer Visual Studio.

> [!IMPORTANT]
> N’utilisez pas la fonctionnalité « Tout télécharger, puis installer » pour créer un cache hors connexion que vous souhaitez transférer vers un autre ordinateur. Cela n’est pas conçu pour fonctionner de cette façon. <br><br>Si vous souhaitez créer un cache hors connexion sur l’ordinateur local que vous pouvez ensuite utiliser pour installer Visual Studio, consultez la section [utiliser la ligne de commande pour créer un cache local](#use-the-command-line-to-create-a-local-cache) ci-dessous.  La page [créer une installation réseau de Visual Studio](../install/create-a-network-installation-of-visual-studio.md) fournit également des informations sur la création d’un cache sur le réseau.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Utiliser la ligne de commande pour créer un cache local
::: moniker range="vs-2017"

Après avoir téléchargé un petit programme d’amorçage, utilisez la ligne de commande pour créer un cache local. Utilisez ensuite le cache local pour installer Visual Studio. (Ce processus remplace les fichiers ISO qui étaient disponibles pour les versions précédentes). 

::: moniker-end

::: moniker range=">=vs-2019"

Après avoir téléchargé un petit fichier de programme d’amorçage, utilisez la ligne de commande pour créer un cache local. Utilisez ensuite le cache local pour installer Visual Studio.

::: moniker-end

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Étape 1 : Télécharger le programme d’amorçage de Visual Studio

Vous devez avoir une connexion Internet pour terminer cette étape.

::: moniker range="vs-2017"

Pour obtenir le dernier programme d’amorçage pour Visual Studio 2017 version 15,9, accédez à la page [versions précédentes de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) et téléchargez l’un des fichiers de programme d’amorçage suivants :

| Édition                                      | Nom de fichier            |
|----------------------------------------------|---------------------|
| Visual Studio Professional 2017 version 15,9 | vs_professional.exe |
| Visual Studio Enterprise 2017 version 15,9   | vs_enterprise.exe   |
| Visual Studio Build Tools 2017 version 15,9  | vs_buildtools.exe   |

::: moniker-end

::: moniker range="vs-2019"

Commencez par Télécharger le programme d’amorçage de Visual Studio 2019 à partir de la [page téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) ou de la page [versions de Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) pour la version et l’édition de Visual Studio que vous avez choisies. Votre fichier d’installation &mdash; ou programme d’amorçage &mdash; correspond à l’un des éléments suivants :

| Édition                         | Fichier                                                                                                                                                                                                                               |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Outils de génération Visual Studio 2019  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
> Les versions commercialisées de Visual Studio 2022 ne sont pas encore disponibles, les programmes d’amorçage ci-dessous concernent la version préliminaire de Visual Studio 2022.
>Commencez par Télécharger le programme d’amorçage de Visual Studio 2022 à partir de la [page de téléchargements Visual Studio](https://aka.ms/vs2022preview).

| Édition                         | Télécharger                                                            |
|---------------------------------|---------------------------------------------------------------------|
| Visual Studio 2022 professionnel | [vs_professional.exe](https://aka.ms/vs/17/pre/vs_professional.exe) |
| Visual Studio 2022 Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/pre/vs_enterprise.exe)     |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Si vous avez précédemment téléchargé un fichier de programme d’amorçage et que vous souhaitez vérifier la version, voici comment procéder. Dans Windows, ouvrez l’Explorateur de fichiers, cliquez avec le bouton droit sur le fichier du programme d’amorçage, choisissez **Propriétés**, cliquez sur l’onglet **Détails** , puis affichez le numéro de **version du produit** . Pour faire correspondre ce nombre à une version de Visual Studio, reportez-vous à la page [numéros de build et dates de publication de Visual Studio](/visual-studio-build-numbers-and-release-dates.md) .

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Si vous avez précédemment téléchargé un fichier de programme d’amorçage et que vous souhaitez vérifier sa version, voici comment procéder. Dans Windows, ouvrez l’Explorateur de fichiers, cliquez avec le bouton droit sur le fichier du programme d’amorçage, choisissez **Propriétés**, cliquez sur l’onglet **Détails** , puis affichez le numéro de **version du produit** . Pour faire correspondre ce nombre à une version de Visual Studio, reportez-vous à la page des [versions de Visual studio 2019](/visualstudio/releases/2019/history) .

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Si vous avez précédemment téléchargé un fichier de programme d’amorçage et que vous souhaitez vérifier sa version, voici comment procéder. Dans Windows, ouvrez l’Explorateur de fichiers, cliquez avec le bouton droit sur le fichier du programme d’amorçage, choisissez **Propriétés**, cliquez sur l’onglet **Détails** , puis affichez le numéro de **version du produit** . Pour faire correspondre ce nombre à une version de Visual Studio, reportez-vous à la page des [versions de Visual studio 2022](/visualstudio/releases/2022/history) .

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>Étape 2 : Créer un cache d’installation local

Vous devez avoir une connexion Internet pour terminer cette étape.

Ouvrez une invite de commandes et utilisez les paramètres du programme d’amorçage tels que définis dans la page [utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md) afin de créer votre cache d’installation local. Des exemples courants d’utilisation du programme d’amorçage d’entreprise sont illustrés ci-dessous et dans la page [exemples de paramètres de ligne de commande](command-line-parameter-examples.md) . Vous pouvez installer une autre langue que l’anglais en modifiant `en-US` les paramètres régionaux dans la [liste des paramètres régionaux de langue](#list-of-language-locales), et vous pouvez utiliser la [liste des composants et des charges de travail](workload-and-component-ids.md) pour personnaliser davantage votre cache.

> [!TIP]
> Pour éviter toute erreur, vérifiez que votre chemin d’installation complet fait moins de 80 caractères.

- Pour le développement d’applications de bureau .NET et web .NET, exécutez :

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Pour le développement d’applications de bureau .NET et Office, exécutez :

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Pour le développement d’applications de bureau C++, exécutez :

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Pour créer une disposition locale complète, en anglais uniquement, avec toutes les fonctionnalités (cela prend beaucoup de temps, &mdash; nous avons _beaucoup_ de fonctionnalités !), exécutez :

   ```shell
    vs_enterprise.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Une disposition Visual Studio complète nécessite un minimum de 35 Go d’espace disque. Pour plus d’informations, consultez [Configuration système requise](/visualstudio/productinfo/vs2017-system-requirements-vs/). 

::: moniker-end

::: moniker range=">=vs-2019"

   > [!NOTE]
   > Une disposition Visual Studio complète nécessite un minimum de 35 Go d’espace disque. Pour plus d’informations, consultez [Configuration système requise](/visualstudio/releases/2019/system-requirements/).

::: moniker-end


### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Étape 3 : Installer Visual Studio à partir du cache local
Quand vous installez Visual Studio à partir d’un cache d’installation local, le programme d’installation de Visual Studio utilise les versions en cache local des fichiers. Toutefois, si vous sélectionnez des composants au cours de l’installation qui ne se trouvent pas dans le cache, le programme d’installation de Visual Studio tente de les télécharger à partir d’Internet. Pour vous assurer que vous installez uniquement les fichiers que vous avez téléchargés précédemment, utilisez les mêmes [options de ligne de commande](use-command-line-parameters-to-install-visual-studio.md) que celles que vous avez utilisées pour créer le cache de disposition. 

Par exemple, si vous avez créé un cache d’installation local à l’aide de la commande suivante :

```shell
vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Utilisez ensuite cette commande pour exécuter l’installation :

```shell
c:\vslayout\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!IMPORTANT]
> Si vous utilisez Visual Studio Community, vous devez l’activer en vous connectant au produit dans les 30 jours suivant l’installation. L’activation requiert une connexion Internet.

> [!NOTE]
> Si vous recevez une erreur indiquant qu’une signature n’est pas valide, vous devez [installer les certificats mis à jour](install-certificates-for-visual-studio-offline.md). Ouvrez le dossier des certificats dans votre cache hors connexion. Double-cliquez sur chacun des fichiers de certificat, puis suivez les étapes de l’Assistant du Gestionnaire de certificats. Si un mot de passe vous est demandé, n’indiquez rien.

::: moniker range=">=vs-2019"
> [!TIP]
> Pour les installations hors connexion, si vous recevez un message d’erreur indiquant « un produit correspondant aux paramètres suivants est introuvable », vérifiez que vous utilisez le `--noweb` commutateur avec la version 16.3.5 ou ultérieure.

::: moniker-end

### <a name="list-of-language-locales"></a>Liste des paramètres régionaux de langue

| **Paramètres régionaux de langue** | **Langage**          |
|---------------------|-----------------------|
| cs-CZ               | Tchèque                 |
| de-DE               | Allemand                |
| fr-FR               | Anglais               |
| es-ES               | Espagnol               |
| fr-FR               | Français                |
| it-IT               | Italien               |
| ja-JP               | Japonais              |
| ko-KR               | Coréen                |
| pl-PL               | Polonais                |
| pt-br               | Portugais - Brésil   |
| ru-RU               | Russe               |
| tr-TR               | Turc               |
| zh-CN               | Chinois - simplifié  |
| zh-TW               | Chinois - traditionnel |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

- [Créer une installation réseau de Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)

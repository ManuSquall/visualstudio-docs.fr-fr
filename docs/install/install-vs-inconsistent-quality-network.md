---
title: Installer dans des environnements réseau à faible bande passante ou non fiables | Microsoft Docs
description: Découvrez comment utiliser Visual Studio Installer quand votre réseau n’est pas fiable ou que votre bande passante est faible, et comment utiliser la ligne de commande pour télécharger les fichiers d’installation.
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio
- no internet connection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: b273efb06e7b2e70617d28dcafc85735bcfb1fd1
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138798"
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Installer Visual Studio 2017 dans des environnements réseau à faible bande passante ou non fiables

Nous vous recommandons d’essayer le programme d’installation web de Visual Studio. Nous pensons qu’il répondra à vos besoins dans la plupart des situations.

 > [!div class="button"]
 > [Télécharger Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

Toutefois, si votre connexion Internet n’est pas disponible ou n’est pas fiable, vous pouvez utiliser la ligne de commande pour créer un cache local des fichiers dont vous avez besoin pour effectuer une installation hors connexion. Voici comment procéder.

> [!NOTE]
> Si vous êtes administrateur d’entreprise et que vous souhaitez effectuer un déploiement de Visual Studio 2017 sur un réseau de stations de travail clientes qui sont protégées d’Internet par un pare-feu, consultez nos pages [Créer une installation réseau de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) et [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>Étape 1 : Télécharger le programme d’amorçage de Visual Studio

Commencez par télécharger le programme d’amorçage de Visual Studio pour l’édition de Visual Studio que vous avez choisie.

Le fichier de votre programme d’installation&mdash;ou pour être plus précis, un fichier de programme d’amorçage&mdash; correspond ou est semblable à l’une des valeurs suivantes.

| Édition                    | Fichier                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Communauté Visual Studio    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>Étape 2 : Créer un cache d’installation local

Vous devez avoir une connexion Internet pour effectuer cette étape. Pour créer une disposition locale, ouvrez une invite de commandes et utilisez l’une des commandes dans les exemples suivants. Ces exemples supposent que vous utilisez l’édition Community de Visual Studio ; adaptez la commande en fonction de votre édition.

- Pour le développement d’applications de bureau .NET et web .NET, exécutez :

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- Pour le développement d’applications de bureau .NET et Office, exécutez :

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Pour le développement d’applications de bureau C++, exécutez :

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Pour créer une disposition locale complète avec toutes les fonctionnalités (cela prendra un certain temps &mdash; nous avons _beaucoup_ de fonctionnalités !), exécutez ceci :

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Si vous souhaitez installer une langue autre que l’anglais, remplacez `en-US` par des paramètres régionaux dans la liste en bas de cette page. Utilisez cette [liste des composants et charges de travail disponibles](workload-and-component-ids.md) pour personnaliser davantage votre cache d’installation si nécessaire.

> [!IMPORTANT]
> Une disposition Visual Studio 2017 complète nécessite au moins 35 Go d’espace disque et peut être assez longue à télécharger. Pour plus d’informations sur la création d’une disposition comprenant uniquement les composants que vous souhaitez installer, consultez [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md).

## <a name="step-3---install-visual-studio-from-the-local-cache"></a>Étape 3 : Installer Visual Studio à partir du cache local

> [!TIP]
> Quand vous procédez à l’exécution à partir d’un cache d’installation local, le programme d’installation utilise les versions locales de chacun de ces fichiers. Toutefois, si vous sélectionnez lors de l’installation des composants qui ne sont pas dans le cache, nous tentons de les télécharger à partir d’Internet.

Pour vérifier que vous installez uniquement les fichiers que vous avez téléchargés, utilisez les mêmes options de ligne de commande que celles utilisées pour créer le cache de disposition. Par exemple, si vous avez créé un cache de disposition avec la commande suivante :

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Utilisez cette commande pour exécuter l’installation :

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> Si vous obtenez une erreur indiquant qu’une signature n’est pas valide, vous devez installer les certificats mis à jour. Ouvrez le dossier des certificats dans votre cache hors connexion. Double-cliquez sur chacun des fichiers de certificat, puis suivez les étapes de l’Assistant du Gestionnaire de certificats. Si le système vous demande un mot de passe, laissez-le vide.

## <a name="list-of-language-locales"></a>Liste des paramètres régionaux de langue

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

* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID de charge de travail et de composant Visual Studio 2017](workload-and-component-ids.md)

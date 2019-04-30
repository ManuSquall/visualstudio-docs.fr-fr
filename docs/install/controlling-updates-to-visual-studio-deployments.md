---
title: Contrôler les mises à jour applicables aux déploiements
description: Découvrez comment changer l’emplacement où Visual Studio recherche une mise à jour dans le cas d’une installation à partir d’un réseau.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d4ce4621fc2fa32f2730c0ce6cdd0618a44386b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974184"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau

Les administrateurs d’entreprise créent souvent une disposition qu’ils hébergent sur un partage de fichiers réseau en vue d’un déploiement pour les utilisateurs finaux.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Contrôle de l’emplacement où Visual Studio recherche des mises à jour

Par défaut, Visual Studio continue de rechercher en ligne des mises à jour même si l’installation a été déployée à partir d’un partage réseau. Si une mise à jour est disponible, l’utilisateur peut l’installer. Tout contenu mis à jour qui ne se trouve pas dans la disposition en mode hors connexion est téléchargée à partir du web.

Si vous souhaitez un contrôle direct sur l’emplacement où Visual Studio recherche les mises à jour, vous pouvez changer l’emplacement où il effectue sa recherche. Vous pouvez également déterminer la version avec laquelle vos utilisateurs sont mis à jour. Pour cela, suivez ces étapes :

1. Créez une disposition en mode hors connexion :

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Copiez-la dans le partage de fichiers dans lequel vous souhaitez l’héberger :

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Modifiez le fichier response.json dans la disposition et modifiez la valeur `channelUri` pour qu’elle pointe vers une copie de channelManifest.json que contrôle l’administrateur.

   Veillez à placer une séquence d’échappement avec les barres obliques inverses dans la valeur, comme dans l’exemple suivant :

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Les utilisateurs finaux peuvent maintenant exécuter le programme d’installation à partir de ce partage pour installer Visual Studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Quand un administrateur d’entreprise détermine que le moment est venu pour les utilisateurs d’effectuer une mise à jour vers une version plus récente de Visual Studio, il peut [mettre à jour l’emplacement de la disposition](update-a-network-installation-of-visual-studio.md) pour intégrer les fichiers mis à jour, comme suit.

1. Utilisez une commande semblable à la commande suivante :

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Vérifiez que le fichier response.json de la disposition mise à jour contient toujours vos personnalisations, en particulier la modification de channelUri, comme suit :

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Les installations existantes de Visual Studio à partir de cette disposition recherchent les mises à jour sur `\\server\share\VS\ChannelManifest.json`. Si le fichier channelManifest.json est plus récent que celui que l’utilisateur a installé, Visual Studio informe l’utilisateur qu’une mise à jour est disponible.

   Les nouvelles installations installent automatiquement la version mise à jour de Visual Studio, directement à partir de la disposition.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Contrôle des notifications dans l’IDE de Visual Studio

::: moniker range="vs-2017"

Comme décrit plus haut, Visual Studio vérifie l’emplacement à partir duquel il a été installé, tel qu’un partage réseau ou via Internet, pour voir si des mises à jour sont disponibles. Quand une mise à jour est disponible, Visual Studio avertit l’utilisateur au moyen d’un indicateur de notification affiché en haut à droite de la fenêtre.

   ![Indicateur de notification des mises à jour](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Comme décrit plus haut, Visual Studio vérifie l’emplacement à partir duquel il a été installé, tel qu’un partage réseau ou via Internet, pour voir si des mises à jour sont disponibles. Quand une mise à jour est disponible, Visual Studio avertit l’utilisateur par une icône de notification en bas à droite de la fenêtre.

   ![Icône de notification dans l’IDE de Visual Studio](media/vs-2019/notification-bar.png "Icône de notification dans l’IDE de Visual Studio")

::: moniker-end

Vous pouvez désactiver les notifications si vous ne souhaitez pas que les utilisateurs finaux soient avertis des mises à jour. (Par exemple, si vous fournissez des mises à jour via un mécanisme de distribution de logiciels central.)

::: moniker range="vs-2017"

Comme Visual Studio 2017 [stocke les entrées de Registre dans un Registre privé](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), vous ne pouvez pas modifier directement le Registre de la façon habituelle. Toutefois, Visual Studio comprend un utilitaire `vsregedit.exe` que vous pouvez utiliser pour modifier les paramètres de Visual Studio. Vous pouvez désactiver les notifications avec la commande suivante :

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Comme Visual Studio 2019 [stocke les entrées de Registre dans un registre privé](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), vous ne pouvez pas modifier directement le Registre de la façon habituelle. Toutefois, Visual Studio comprend un utilitaire `vsregedit.exe` que vous pouvez utiliser pour modifier les paramètres de Visual Studio. Vous pouvez désactiver les notifications avec la commande suivante :

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Veillez à remplacer le répertoire pour faire correspondre l’instance installée que vous souhaitez modifier.)

> [!TIP]
> Utilisez [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) pour rechercher une instance spécifique de Visual Studio sur une station de travail cliente.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Outils de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Cycle de vie et maintenance des produits Visual Studio](/visualstudio/releases/2019/servicing/)
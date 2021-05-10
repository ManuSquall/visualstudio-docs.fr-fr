---
title: Contrôler les mises à jour applicables aux déploiements
description: Découvrez comment changer l’emplacement où Visual Studio recherche une mise à jour dans le cas d’une installation à partir d’un réseau.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3504e866a7f89de8fa38f92a8bfea501ddd952c9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666794"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau

Les administrateurs d’entreprise créent souvent une disposition et l’hébergent sur un partage de fichiers réseau pour le déploiement sur leurs utilisateurs finaux. Cette page explique comment configurer correctement les options de disposition du réseau. 

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Contrôle de l’emplacement où Visual Studio recherche des mises à jour

**Scénario 1 : le client a été installé à l’origine à partir d’une disposition, mais il est configuré pour recevoir des mises à jour à partir de l’emplacement de la disposition du réseau ou du Web**

Par défaut, Visual Studio continue de rechercher en ligne les mises à jour même si l’installation a été déployée à l’origine à partir d’un partage réseau. Si une mise à jour est disponible sur le Web, l’utilisateur peut l’installer. Bien que le cache de présentation réseau soit examiné en premier pour tous les bits de produit mis à jour, s’ils ne sont pas trouvés là, Visual Studio recherchera et téléchargera les bits du produit mis à jour à partir du Web.

**Scénario 2 : le client a installé à l’origine et doit recevoir uniquement les mises à jour de la disposition du réseau**

Si vous souhaitez contrôler l’endroit où le client Visual Studio recherche des mises à jour, par exemple, si votre ordinateur client n’a pas accès à Internet et que vous souhaitez vous assurer qu’il est installé uniquement et qu’il s’installe toujours à partir de la disposition, vous pouvez configurer l’emplacement où le programme d’installation du client recherche les bits du produit mis à jour. Il est préférable de s’assurer que ce paramètre est correctement configuré avant que le client effectue l’installation initiale à partir de la disposition. 

1. Créez une disposition en mode hors connexion :

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Copiez-la dans le partage de fichiers dans lequel vous souhaitez l’héberger :

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Modifiez le `response.json` fichier dans la disposition et modifiez la `channelUri` valeur pour qu’elle pointe vers une copie de l' channelManifest.jssur ce contrôle d’administration.

   Veillez à placer une séquence d’échappement avec les barres obliques inverses dans la valeur, comme dans l’exemple suivant :

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Désormais, les utilisateurs finaux peuvent exécuter le programme d’installation à partir de ce partage pour installer Visual Studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Quand un administrateur d’entreprise détermine que le moment est venu pour les utilisateurs d’effectuer une mise à jour vers une version plus récente de Visual Studio, il peut [mettre à jour l’emplacement de la disposition](update-a-network-installation-of-visual-studio.md) pour intégrer les fichiers mis à jour, comme suit.

1. Utilisez une commande semblable à la commande suivante :

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Assurez-vous que le `response.json` fichier dans la disposition mise à jour contient toujours vos personnalisations, en particulier la modification channelUri, comme suit :

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

Les installations existantes de Visual Studio à partir de cette disposition recherchent les mises à jour sur `\\server\share\VS\ChannelManifest.json`. Si le fichier channelManifest.json est plus récent que celui que l’utilisateur a installé, Visual Studio informe l’utilisateur qu’une mise à jour est disponible.

Toute mise à jour d’installation lancée à partir du client installera automatiquement la version mise à jour de Visual Studio directement à partir de la disposition.

**Scénario 3 : le client a été installé à l’origine à partir du Web, mais ne doit recevoir des mises à jour qu’à partir d’une disposition réseau**

Dans certains cas, l’ordinateur client a peut-être déjà installé Visual Studio à partir du Web, mais l’administrateur souhaite à présent que toutes les mises à jour ultérieures proviennent d’une disposition gérée. La seule méthode prise en charge pour cela consiste à créer une disposition réseau avec la version souhaitée du produit, puis sur l’ordinateur client, à exécuter le programme _d’amorçage à partir de l’emplacement_ de la disposition (par exemple, `\\server\share\vs_enterprise.exe` ). Dans l’idéal, l’installation originale du client s’est produite à l’aide du programme d’amorçage de la disposition du réseau avec le ChannelURI correctement configuré, mais l’exécution du programme d’amorçage mis à jour à partir de l’emplacement de la disposition du réseau fonctionne également. L’une de ces actions entraînerait l’incorporation, sur l’ordinateur client, d’une connexion avec cet emplacement de disposition particulier. Le seul inconvénient de ce scénario est que le « ChannelURI » dans le fichier de la disposition `response.json` doit être le même que le ChannelURI défini sur l’ordinateur du client lors de l’installation d’origine. Cette valeur a probablement été définie à l’origine sur le [canal de publication](https://aka.ms/vs/16/release/channel)Internet. 


## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Contrôle des notifications dans l’IDE de Visual Studio

::: moniker range="vs-2017"

Comme décrit plus haut, Visual Studio vérifie l’emplacement à partir duquel il a été installé, tel qu’un partage réseau ou via Internet, pour voir si des mises à jour sont disponibles. Quand une mise à jour est disponible, Visual Studio avertit l’utilisateur au moyen d’un indicateur de notification affiché en haut à droite de la fenêtre.

   ![Indicateur de notification des mises à jour](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019&quot;

Comme décrit plus haut, Visual Studio vérifie l’emplacement à partir duquel il a été installé, tel qu’un partage réseau ou via Internet, pour voir si des mises à jour sont disponibles. Quand une mise à jour est disponible, Visual Studio avertit l’utilisateur par une icône de notification en bas à droite de la fenêtre.

   ![Icône de notification dans l’IDE de Visual Studio](media/vs-2019/notification-bar.png &quot;Icône de notification dans l’IDE de Visual Studio")

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

* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Activation des mises à jour de l’administrateur](enabling-administrator-updates.md)
* [Application des mises à jour de l’administrateur](applying-administrator-updates.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Outils de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Maintenance et cycle de vie des produits Visual Studio](/visualstudio/releases/2019/servicing/)

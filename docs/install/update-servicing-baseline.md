---
title: Mettre à jour Visual Studio tout en étant sur une ligne de base de maintenance
description: Découvrez comment mettre à jour Visual Studio tout en étant sur une ligne de base de maintenance.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: '>=vs-2019'
ms.openlocfilehash: 03a192657a46c2db15cb2d1121735905f06da478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306668"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Mettre à jour Visual Studio tout en étant sur une ligne de base de maintenance

Nous mettons souvent à jour Visual Studio au cours du cycle de vie du produit. Il existe deux types de mise à jour :

* **Mises à jour** &mdash; de version mineures par exemple, 16,0 à 16,1 &mdash; qui incluent de nouveaux composants et fonctionnalités.  
* **Mises à jour de maintenance**, par exemple de la 16.0.4 à la 16.0.5, qui incluent uniquement les correctifs ciblés pour les problèmes critiques.

Les administrateurs d’entreprise peuvent choisir de conserver leurs clients sur une base de référence de maintenance. Une base de référence de maintenance inclut des mises à jour pour une année au-delà de la base de référence de maintenance suivante.

L’option de base de référence de maintenance offre plus de flexibilité aux développeurs et administrateurs, qui peuvent ainsi intégrer les nouvelles fonctionnalités, les correctifs de bogues ou les composants inclus dans les nouvelles mises à jour mineures. La première base de référence de maintenance est 16.0.x. Pour plus d’informations, consultez [Options de support pour les clients Enterprise et Professional](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Comment bénéficier d’une base de référence de maintenance

Pour démarrer avec une base de référence de maintenance, téléchargez une version corrigée du programme d’amorçage du programme d’installation de Visual Studio sur [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Les programmes d’amorçage comportent des liens vers les configurations de produits, les charges de travail et les composants de cette version spécifique.

> [!NOTE]
> Veillez à faire la distinction entre la version corrigée du programme d’amorçage et les programmes d’amorçage standard. Les programmes d’amorçage standard sont configurés pour utiliser la dernière version disponible de Visual Studio. Leur nom de fichier comporte un numéro (par exemple : vs_enterprise__123456789-123456789.exe) lorsqu’ils sont téléchargés depuis My.VisualStudio.com.

Lors de l’installation, les administrateurs d’entreprise doivent configurer leurs clients pour les empêcher d’effectuer une mise à jour avec la dernière version. Pour ce faire, plusieurs méthodes sont possibles :
- [Modifiez le paramètre `channelUri` dans le fichier de configuration de réponse](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) pour utiliser un manifeste de canal dans la disposition ou le dossier local.
- [Modifiez l’URI de canal via l’exécution de ligne de commande](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) pour utiliser un fichier qui n’existe pas.
- [Définissez des stratégies sur le système client pour désactiver les mises à jour](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating), afin d’empêcher les clients d’effectuer une mise à jour automatique.

### <a name="install-a-servicing-baseline-on-a-network"></a>Installer une base de référence de maintenance sur un réseau

Les administrateurs qui utilisent une installation de disposition de réseau doivent modifier la valeur `channelUri` dans le fichier *response.json* dans la disposition pour utiliser le fichier *channelmanifest.json* qui se trouve dans le même dossier. Pour connaître la procédure à suivre, consultez [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md). La modification de la valeur `channelUri` permet aux clients de rechercher les mises à jour dans l’emplacement de la disposition.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Installer une base de référence de maintenance via Internet

Dans le cas d’une installation basée sur Internet, ajoutez `--channelUri` avec un manifeste de canal inexistant à la ligne de commande utilisée pour lancer le programme d’installation. Cette opération empêche Visual Studio d’utiliser la dernière version disponible d’une mise à jour. Voici un exemple :

```shell
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Utiliser des paramètres de stratégie pour empêcher la mise à jour des clients

Une autre option pour contrôler les mises à jour sur un client consiste à [désactiver les notifications de mise à jour](controlling-updates-to-visual-studio-deployments.md). Utilisez cette option si la valeur du paramètre channelUri n’a pas été modifiée lors de l’installation. Cette option empêche le client de recevoir des liens pointant vers la dernière version disponible. Une version corrigée du programme d’amorçage reste nécessaire pour effectuer une mise à jour avec une version spécifique sur le client.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Comment conserver une base de référence de maintenance

Si une mise à jour d’une base de référence de maintenance est disponible, vous pouvez télécharger les fichiers de la version corrigée du programme d’amorçage pour la mise à jour de maintenance depuis le site [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0).

Les administrateurs qui effectuent un déploiement via une installation réseau doivent mettre à jour l’[emplacement de la disposition](update-a-network-installation-of-visual-studio.md) réseau. Les clients ayant effectué une installation à partir de l’emplacement recevront des notifications de mise à jour. Si la mise à jour doit être déployée sur les clients, suivez [ces instructions](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines). Quand vous modifiez le fichier « response.json » pour une mise à jour, n’ajoutez pas de charges de travail, de composants ou de langages supplémentaires. La gestion de ces paramètres doit être effectuée dans un déploiement de « modification » une fois le produit mis à jour.

Dans le cas d’une installation basée sur Internet, exécutez la nouvelle version corrigée du programme d’amorçage avec le paramètre `--channelUri` pointant vers un manifeste de canal inexistant sur le client. Si la mise à jour est déployée en mode silencieux ou passif, utilisez deux commandes distinctes :

1. Mettez à jour le programme d’installation de Visual Studio :

    ```shell
    vs_enterprise.exe --quiet --update
    ```

::: moniker range="vs-2019"
 
2. Mettez à jour l’application Visual Studio proprement dite :
    ```shell
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

::: moniker-end

::: moniker range=">=vs-2022"

2. Mettez à jour l’application Visual Studio proprement dite :
    ```shell
    vs_enterprise.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Outils de détection et de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Guide pratique pour définir des paramètres dans un fichier réponse](automated-installation-with-response-file.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md)
* [Maintenance et cycle de vie des produits Visual Studio](/visualstudio/releases/2019/servicing/)

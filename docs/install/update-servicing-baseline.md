---
title: Mettre à jour Visual Studio tout en étant sur une ligne de base de maintenance
titleSuffix: ''
description: Découvrez comment mettre à jour Visual Studio tout en étant sur une ligne de base de maintenance.
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: doughall
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 36bbec66e822d7e1daebcadbeeba30e166747368
ms.sourcegitcommit: aeb1a1135dd789551e15aa5124099a5fe3f0f32b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66501122"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Mettre à jour Visual Studio tout en étant sur une ligne de base de maintenance

Visual Studio 2019 recevra de fréquentes mises à jour lors de son [cycle de vie des produits](/visualstudio/productinfo/release-rhythm#release-channel-updates). Cela inclut les mises à jour de version mineures (par exemple : 16.0 vers 16.1) pouvant inclure de nouvelles fonctionnalités et de nouveaux composants, et les mises à jour de maintenance (par exemple : 16.0.4 à 16.0.5) contenant uniquement des correctifs ciblant les problèmes critiques. 

Les administrateurs d’entreprise peuvent choisir de garder leurs clients sur une base de référence de maintenance incluant des mises à jour pour une année au-delà de la base de référence de maintenance suivante. Cela offre plus de flexibilité aux développeurs et administrateurs, qui peuvent ainsi intégrer les nouvelles fonctionnalités, les correctifs de bogues ou les composants inclus dans les nouvelles mises à jour mineures. La première base de référence de maintenance est 16.0.x. Voir [Options de support pour les clients Enterprise et Professional](https://docs.microsoft.com/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) pour plus d'informations.

## <a name="how-to-get-onto-a-servicing-baseline"></a>Comment bénéficier d’une base de référence de maintenance

Pour démarrer avec une base de référence de maintenance, téléchargez une version corrigée du programme d’amorçage de Visual Studio Installer sur [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Ces programmes d’amorçage comportent des liens vers les configurations de produits, les charges de travail et les composants de cette version spécifique. 

> [!NOTE]
> Veillez à faire la distinction entre la version corrigée du programme d’amorçage et les programmes d’amorçage standard. Les programmes d’amorçage standard sont configurés pour utiliser la dernière version disponible de Visual Studio. Leur nom de fichier comporte un numéro (par exemple : vs_enterprise__123456789-123456789.exe) lorsqu’ils sont téléchargés depuis my.visualstudio.com.

Lors de l’installation, les administrateurs d’entreprise doivent configurer leurs clients pour les empêcher d’effectuer une mise à jour avec la dernière version. Pour cela, ils peuvent [modifier le paramètre channelUri dans le fichier de configuration de la réponse](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) pour utiliser un manifeste de canal dans la disposition ou dans un dossier local, [modifier le paramètre channelUri à l’aide d’une ligne de commande](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) pour utiliser un fichier inexistant, ou [définir des stratégies sur le système client pour désactiver les mises à jour](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating) et empêcher la mise à jour automatique des clients. 

### <a name="install-a-servicing-baseline-on-a-network"></a>Installer une base de référence de maintenance sur un réseau

Pour les administrateurs qui gèrent une installation de type réseau, modifiez la valeur du paramètre channelUri de `response.json` dans la disposition afin d’utiliser le fichier channelmanifest.json qui se trouve dans le même dossier. Consultez [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md) pour obtenir des instructions pas à pas. La modification du paramètre channelUri permet aux clients de rechercher les mises à jour dans l’emplacement de la disposition. 

### <a name="install-a-servicing-baseline-via-the-internet"></a>Installer une base de référence de maintenance via Internet

Dans le cas d’une installation basée sur Internet, ajoutez `--channelUri` avec un manifeste de canal inexistant à la ligne de commande utilisée pour lancer le programme d’installation. Cette opération empêche Visual Studio d’utiliser la dernière version disponible d’une mise à jour. Voici un exemple :

  ```cmd
   vs_enterprise.exe --channelUri c:\doesnotexist.chman 
  ```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Utiliser des paramètres de stratégie pour empêcher la mise à jour des clients

Une autre option pour contrôler les mises à jour sur un client consiste à [désactiver les notifications de mise à jour](controlling-updates-to-visual-studio-deployments.md). Utilisez cette option si la valeur du paramètre channelUri n’a pas été modifiée lors de l’installation. Cette option empêche le client de recevoir des liens pointant vers la dernière version disponible. Une version corrigée du programme d’amorçage reste nécessaire pour effectuer une mise à jour avec une version spécifique sur le client.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Comment conserver une base de référence de maintenance

Si une mise à jour d’une base de référence de maintenance est disponible, vous pouvez télécharger les fichiers de la version corrigée du programme d’amorçage pour la mise à jour de maintenance depuis le site [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Ces fichiers peuvent être utilisés dans plusieurs scénarios.

Les administrateurs qui effectuent un déploiement via une installation en réseau peuvent mettre à jour l’[emplacement de la disposition](update-a-network-installation-of-visual-studio.md). Les clients ayant effectué une installation à partir de l’emplacement recevront des notifications de mise à jour. Si la mise à jour doit être déployée sur les clients, suivez [ces instructions](update-a-network-installation-of-visual-studio.md#how-to-deploy-an-update-to-client-machines). Lorsque vous modifiez le fichier response.json dans le cadre d’une mise à jour, n’ajoutez pas d’autres charges de travail, composants ou langages. La gestion de ces paramètres doit être effectuée dans un déploiement de « modification » une fois le produit mis à jour. 

Dans le cas d’une installation basée sur Internet, exécutez la nouvelle version corrigée du programme d’amorçage avec le paramètre `--channelUri` pointant vers un manifeste de canal inexistant sur le client. Si la mise à jour est déployée en mode silencieux ou passif, utilisez deux commandes distinctes :

1. Mettez tout d’abord à jour Visual Studio Installer : <br>```vs_enterprise.exe --quiet --update```
2. Mettez ensuite à jour l’application Visual Studio proprement dite : <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Outils de détection et de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Guide pratique pour définir des paramètres dans un fichier réponse](automated-installation-with-response-file.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md)
* [Cycle de vie et maintenance des produits Visual Studio](/visualstudio/releases/2019/servicing/)

---
title: Sélectionner les emplacements d'installation
description: Découvrez comment réduire l’empreinte de l’installation de Visual Studio sur votre lecteur système en plaçant le cache de téléchargement, les composants partagés, les kits SDK et les outils sur d’autres lecteurs.
ms.date: 11/07/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2acefee22976e061b3feff83b00891037a0f2bbd
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159839"
---
# <a name="select-the-installation-locations-in-visual-studio-2017"></a>Sélectionner les emplacements d’installation dans Visual Studio 2017

**Nouveautés de la version 15.7** : Vous pouvez réduire l’empreinte de l’installation de Visual Studio sur votre lecteur système en changeant l’emplacement de certains de ses fichiers. Plus précisément, vous pouvez utiliser un autre emplacement pour le cache de téléchargement, les composants partagés, les SDK et les fichiers des outils.

   > [!NOTE]
   > L’emplacement d’installation de certains outils et SDK est régi par des règles différentes. Ces outils et SDK sont toujours installés sur votre lecteur système, même si vous choisissez un autre emplacement.

Prêt à commencer ? Voici comment procéder.

1. Quand vous installez Visual Studio, choisissez l’onglet **Emplacements d’installation**.

   ![Visual Studio 2017 : Sélectionner l’emplacement d’installation](media/vs-installation-locations.png "Sélectionner l’emplacement d’installation.")

1. Dans la section **IDE Visual Studio**, acceptez la valeur par défaut. Visual Studio installe le noyau du produit et inclut les fichiers propres à cette version de Visual Studio.

   ![Section IDE Visual Studio de l’onglet Emplacements d’installation](media/vs-installation-locations-ide.png "Acceptez la valeur par défaut pour la section IDE Visual Studio de l’onglet Emplacement d’installation.")

   > [!TIP]
   > Si votre lecteur système est un disque SSD (Solid-State Drive), nous vous recommandons d’accepter l’emplacement par défaut sur votre lecteur système. Pourquoi ? Quand vous développez avec Visual Studio, vous lisez et écrivez un grand nombre de fichiers, ce qui augmente l’activité E/S du disque. Il est conseillé de choisir votre lecteur le plus rapide pour gérer la charge.

1. Dans la section **Cache de téléchargement**, indiquez si vous voulez conserver le cache de téléchargement, puis choisissez où stocker ses fichiers.

     ![Section Cache de téléchargement de l’onglet Emplacements d’installation](media/vs-installation-locations-cache.png "Choisissez s’il faut conserver le cache de téléchargement après l’installation, puis spécifiez le lecteur où stocker les fichiers.")

    1. Cochez ou décochez **Conserver le cache de téléchargement après l’installation**.

       Si vous décidez de ne pas conserver le cache de téléchargement, l’emplacement n’est utilisé que temporairement. Cette action n’affecte ni ne supprime les fichiers des installations précédentes.

    1. Spécifiez le lecteur où stocker les fichiers et manifestes d’installation du cache de téléchargement.

        Par exemple, si vous sélectionnez la charge de travail « Développement Desktop en C++ », la taille requise temporairement est de 1,58 Go sur votre lecteur système, qui est libérée dès que l’installation est terminée.

       > [!IMPORTANT]
       > L’emplacement est défini avec la première installation et vous ne pouvez plus le changer à partir de l’interface utilisateur du programme d’installation. À la place, vous devez [utiliser des paramètres de ligne de commande](use-command-line-parameters-to-install-visual-studio.md) pour déplacer le cache de téléchargement.

1. Dans la section **Composants partagés, outils et SDK**, spécifiez le lecteur où stocker les fichiers qui sont partagés par les installations côte à côte de Visual Studio. Les SDK et les outils sont également stockés dans ce répertoire.

   ![Section Composants partagés, outils et SDK de l’onglet Emplacements d’installation](media/vs-installation-locations-shared.png "Spécifiez l’emplacement où stocker les composants partagés, les outils et les SDK.")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio 2017](install-visual-studio.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
* [Modifier Visual Studio 2017](update-visual-studio.md)
* [Désinstaller Visual Studio 2017](uninstall-visual-studio.md)

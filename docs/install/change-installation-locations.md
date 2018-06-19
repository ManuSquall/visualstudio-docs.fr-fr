---
title: Changer les emplacements d’installation dans Visual Studio 2017
description: Découvrez comment réduire l’empreinte de l’installation sur votre lecteur système en changeant l’emplacement du cache de téléchargement, des composants partagés, des kits SDK et des outils sur d’autres lecteurs.
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- move installation files to different drives
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eef4f8b66da517e471a25bb36e777f6cc343b0a3
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33995778"
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>Changer les emplacements d’installation dans Visual Studio 2017

**Nouveauté de la version 15.7** : vous pouvez réduire l’empreinte de l’installation sur votre lecteur système en déplaçant le cache de téléchargement, les composants partagés, les kits SDK et les outils sur d’autres lecteurs.

Voici comment procéder.

1. Quand vous installez Visual Studio, choisissez l’onglet **Options d’installation**.

  ![Visual Studio 2017 : changer l’emplacement d’installation](media/installation-options-by-location.png "Changer l’emplacement d’installation")

  > [!IMPORTANT]
  > Si vous interrompez l’installation pour la reprendre plus tard, Visual Studio reprend là où il s’était arrêté. En d’autres termes, la progression de son installation s’applique à ce qu’il reste à télécharger et à installer et ne démarre pas à partir du nombre précédent.

2. Dans la section **IDE Visual Studio**, acceptez la valeur par défaut. Elle permet d’installer le noyau du produit et inclut les fichiers propres à cette version de Visual Studio.

 > [!IMPORTANT]
 > Si votre lecteur système est un disque SSD (Solid-State Drive), voici pourquoi nous vous recommandons d’accepter l’emplacement par défaut sur celui-ci : quand vous développez avec Visual Studio, vos opérations de lecture et d’écriture portent sur un grand nombre de fichiers, ce qui augmente l’activité d’E/S sur disque.  Il est conseillé de choisir votre lecteur le plus rapide pour gérer la charge.

2. Dans la section **Cache de téléchargement**, indiquez si vous souhaitez conserver le cache de téléchargement, puis cochez ou décochez la case **Conserver le cache de téléchargement après l’installation** en conséquence. <br><br>Si vous décidez de ne pas conserver le cache de téléchargement, l’emplacement n’est utilisé que temporairement. De plus, cette action n’affecte pas ou ne supprime pas les fichiers des installations précédentes. (Pour nettoyer tous les packages d’installation, vous devez modifier vos installations précédentes séparément.)

3. Dans la section **Cache de téléchargement**, spécifiez le lecteur où vous souhaitez stocker les fichiers d’installation et les manifestes. <br><br>Par exemple, si vous sélectionnez la charge de travail « Développement Desktop en C++ », la taille requise temporairement est de 1,58 Go sur votre lecteur système, qui est libérée dès que l’installation est terminée.

 > [!NOTE]
 > Les fichiers sont téléchargés dans un dossier temporaire sur votre lecteur système, puis supprimés une fois que Visual Studio les a vérifiés, puis déplacés vers le dossier du cache de téléchargement. Si vous décidez de conserver votre cache de téléchargement sur un autre lecteur, Visual Studio a toujours besoin d’un espace disque équivalent à la taille du cache de téléchargement sur votre lecteur système.
 > [!IMPORTANT]
 > Une fois l’emplacement défini avec la première installation, vous ne pouvez plus le changer à partir de l’interface utilisateur du programme d’installation. Au lieu de cela, vous devez [utiliser des paramètres de ligne de commande](use-command-line-parameters-to-install-visual-studio.md) pour déplacer le cache de téléchargement.

4. Dans la section **Composants partagés, outils et SDK**, spécifiez le lecteur sur lequel vous souhaitez stocker les fichiers qui sont partagés par les installations de Visual Studio côte à côte. Les kits SDK et les outils qui permettent au programme d’installation de Visual Studio de changer l’emplacement de son installation sont également stockés dans ce répertoire.

 > [!NOTE]
 > L’emplacement de l’installation de certains outils et kits SDK est régi par des règles différentes. Ces outils et kits SDK sont toujours installés sur votre lecteur système, même si vous choisissez un autre emplacement.

## <a name="get-support"></a>Obtenir de l’aide

Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md) pour obtenir de l’aide. Vous pouvez également nous contacter pour obtenir de l’aide sur l’installation par [conversation en direct](https://www.visualstudio.com/vs/support/#talktous) (en anglais uniquement) ; pour plus d’informations, consultez la [page Visual Studio « Contactez-nous »](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :

* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit et obtenir des réponses dans la [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/).
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter](https://gitter.im/Microsoft/VisualStudio). (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio 2017](install-visual-studio.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
* [Modifier Visual Studio 2017](update-visual-studio.md)
* [Désinstaller Visual Studio 2017](uninstall-visual-studio.md)

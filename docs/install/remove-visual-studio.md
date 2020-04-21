---
title: Supprimer Visual Studio
titleSuffix: ''
description: Apprenez à supprimer complètement Visual Studio de votre ordinateur, étape par étape.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 98886df1c7fb09fa30d5c54abe19452780195b6a
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649194"
---
# <a name="remove-visual-studio"></a>Supprimer Visual Studio

Si vous rencontrez une erreur catastrophique et que vous ne pouvez `InstallCleanup.exe` pas réparer ou désinstaller Visual Studio, vous pouvez exécuter l’outil pour supprimer les fichiers d’installation et les informations sur les produits pour toutes les instances installées de Visual Studio 2017 ou Visual Studio 2019.

> [!WARNING]
> Utilisez l’outil InstallCleanup **uniquement en dernier recours** si la réparation ou le désinstallation échouent. Cet outil pourrait désinstaller les fonctionnalités d’autres installations visual Studio ou d’autres produits, qui pourraient alors également avoir besoin d’être réparés ou réinstallés.

## <a name="run-installcleanupexe"></a>Exécuter InstallCleanup.exe

Vous pouvez utiliser l’un ou l’autre des commutateurs de ligne de commande suivants avec l’outil `InstallCleanup.exe` :

| Commutateur | Comportement |
| ------ | -------- |
| `-i`   | Ce commutateur est par défaut si aucun autre commutateur n’est passé. Il supprime uniquement l’annuaire d’installation principal et les informations sur les produits. Utilisez ce commutateur si vous avez l’intention de réinstaller la même version de Visual Studio après avoir exécuté l’outil. `InstallCleanup.exe` |
| `-f`   | Ce commutateur supprime le répertoire d’installation principal, les informations sur les produits et la plupart des autres fonctionnalités installées à l’extérieur du répertoire d’installation, qui pourraient également être partagés avec d’autres installations visual Studio ou d’autres produits. Utilisez ce commutateur si vous avez l’intention de supprimer Visual Studio sans le réinstaller plus tard. |

Voici comment faire fonctionner `InstallCleanup.exe` l’outil :

1. Fermez le programme d’installation de Visual Studio.
1. Ouvrez une invite de commandes d'administrateur. Pour ouvrir une invite de commandes administrateur, suivez les étapes ci-dessous :
   * Tapez **cmd** dans la zone « Tapez ici pour effectuer une recherche ».
   * Cliquez avec le bouton droit sur **Invite de commandes**, puis sélectionnez **Exécuter en tant qu’administrateur**.
1. Entrez le chemin `InstallCleanup.exe` complet de l’outil et ajoutez l’interrupteur de ligne de commande que vous préférez. Par défaut, le chemin de l’outil est le suivant. Les citations doubles entourent une commande contenant des espaces :

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Si vous ne `InstallCleanup.exe` pouvez pas trouver sous le répertoire Visual `%ProgramFiles(x86)%\Microsoft Visual Studio`Studio Installer, qui est toujours situé à , voici ce qu’il faut faire ensuite. Suivez les instructions pour [installer Visual Studio](install-visual-studio.md). Ensuite, lorsque l’écran de sélection de la charge de travail est affiché, fermez la fenêtre et suivez à nouveau les étapes de cette page.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
* [Modifier Visual Studio 2017](modify-visual-studio.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)

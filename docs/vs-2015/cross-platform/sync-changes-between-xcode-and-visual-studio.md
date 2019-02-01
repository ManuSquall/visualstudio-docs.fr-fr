---
title: Synchroniser les modifications entre XCode et Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: bb7b5ebe398b66a8ae28d7734d64ce67c8735a73
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754912"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Synchroniser les modifications entre Xcode et Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Le composant Microsoft Visual C++ pour le développement mobile comprend des fonctionnalités distantes qui permettent de synchroniser le travail entre votre PC et votre Mac. Quand vos machines Visual Studio et Mac sont jumelées, de nouvelles options disponibles pour les projets d’application iOS dans Visual Studio vous permettent d’ouvrir votre projet dans Xcode, de déplacer votre code entre Xcode et Visual Studio et de nettoyer le répertoire de projet Xcode temporaire.

 Pour permettre l’utilisation des options de machine distante, votre projet doit être un projet d’application iOS, et Visual Studio doit être jumelé à votre Mac. Pour connaître les prérequis et obtenir des instructions sur le jumelage à un Mac, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>Menu Machine distante
 Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur un projet d’application iOS pour afficher le menu contextuel. Sélectionnez l’élément **Machine distante** pour afficher les options distantes disponibles.

 ![Élément de menu Machine distante dans l’Explorateur de solutions](../cross-platform/media/cppmdd-u2-remotemachine-menu.jpg "CPPMDD_U2_RemoteMachine_Menu")

 Ces commandes vous permettent d’ouvrir votre projet dans Xcode, de déplacer des changements locaux ou l’ensemble du projet entre Visual Studio et Xcode, et de nettoyer les fichiers temporaires sur la machine distante.

### <a name="open-in-xcode"></a>Ouvrir dans Xcode
 Pour ouvrir le projet dans Xcode à partir de Visual Studio, dans le sous-menu **Machine distante**, choisissez **Ouvrir dans Xcode** afin d’ouvrir le projet sélectionné sur la machine distante jumelée. Le serveur vcremote permet d’ouvrir Xcode et d’accéder à un répertoire temporaire créé sur votre Mac, qui contient une copie du projet. Visual Studio affiche une boîte de dialogue qui indique le répertoire temporaire utilisé pour le projet. Les actions effectuées sur la machine distante sont également affichées dans la fenêtre **Sortie** de Visual Studio. Pour les voir, vous devrez peut-être sélectionner **Machine distante Visual C++** dans la liste déroulante **Afficher la sortie à partir de** en haut de la fenêtre **Sortie**.

 ![La fenêtre Sortie affiche les actions de la machine distante.](../cross-platform/media/cppmdd-u2-remotemachine-output.png "CPPMDD_U2_RemoteMachine_Output")

 Sur votre Mac, vous pouvez utiliser tous les outils Xcode pour modifier votre code, vos ressources, vos storyboards et vos actions. Dans Visual Studio, votre projet d’application iOS est annoté avec « Ouvert dans Xcode » pour indiquer que des changements peuvent être effectués sur la machine distante. Une fois vos modifications effectuées, vous pouvez utiliser les commandes Pull à partir de l’emplacement distant ou Pull incrémentiel à partir de l’emplacement distant pour copier ces changements dans votre projet Visual Studio.

### <a name="push-to-remote-and-incremental-push-to-remote"></a>Push vers l’emplacement distant et Push incrémentiel vers l’emplacement distant
 Si vous avez apporté des changements à votre projet d’application iOS dans Visual Studio, les commandes Push vers l’emplacement distant et Push incrémentiel vers l’emplacement distant peuvent vous permettre de déplacer les fichiers projet modifiés vers la machine distante jumelée. La commande Push vers l’emplacement distant copie tous les fichiers projet vers la machine distante. La commande Push incrémentiel vers l’emplacement distant ne copie que les fichiers modifiés vers la machine distante. Pour les grands projets avec de petits changements, la commande Push incrémentiel permet de gagner du temps et d’économiser de la bande passante.

 Pour copier les fichiers projet vers votre Mac, dans Visual Studio, dans la fenêtre de l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet Application iOS pour ouvrir le menu contextuel. Sélectionnez **Machine distante**, choisissez **Push vers l’emplacement distant** ou **Push incrémentiel vers l’emplacement distant** pour copier les fichiers projet de Visual Studio vers votre Mac.

### <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Pull à partir de l’emplacement distant et Pull incrémentiel à partir de l’emplacement distant
 Après avoir apporté des changements à votre projet dans Xcode, appliquez-les dans Visual Studio pour garder les projets synchronisés.

 Pour copier les fichiers projet depuis votre Mac, dans Visual Studio, dans la fenêtre de l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet Application iOS pour ouvrir le menu contextuel. Sélectionnez **Machine distante**, choisissez **Pull à partir de l’emplacement distant** ou **Pull incrémentiel à partir de l’emplacement distant** pour copier les fichiers projet de votre Mac vers Visual Studio.

### <a name="clean-remote"></a>Nettoyer la machine distante
 Vous pouvez utiliser la commande Nettoyer la machine distante pour supprimer les fichiers du répertoire de projet temporaire sur la machine distante. Le contenu du répertoire, notamment les fichiers sources ou les produits de build, est supprimé de votre Mac. Vérifiez que vous avez synchronisé tous les changements que vous souhaitez appliquer dans Visual Studio à l’aide des commandes Pull à partir de l’emplacement distant ou Pull incrémentiel à partir de l’emplacement distant, avant d’utiliser la commande Nettoyer la machine distante.

 Pour nettoyer le répertoire de projet temporaire sur la machine distante, dans Visual Studio, dans la fenêtre de l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet Application iOS pour ouvrir le menu contextuel. Sélectionnez **Machine distante**, puis choisissez **Nettoyer la machine distante** pour supprimer les fichiers du répertoire de projet de votre Mac.

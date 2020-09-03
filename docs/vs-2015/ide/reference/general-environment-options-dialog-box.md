---
title: Général, Environnement, boîte de dialogue Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83fc6adeba0529be03a9a982713d0584a2a7bc45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661273"
---
# <a name="general-environment-options-dialog-box"></a>Général, Environnement, boîte de dialogue Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez cette page pour modifier les thèmes de couleurs, les paramètres de la barre d'état et les associations d'extensions de fichier, entre autres options, pour l'environnement de développement intégré (IDE). Vous pouvez accéder à la boîte de dialogue **Options** en ouvrant le menu **Outils**, en choisissant **Options**, en ouvrant le dossier **Environnement**, puis en choisissant la page **Général**. Si cette page n’apparaît pas dans la liste, cochez la case **Afficher tous les paramètres** dans la boîte de dialogue **Options**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour changer vos paramètres, ouvrez le menu **Outils**, puis choisissez **Importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="visual-experience"></a>Expérience visuelle
 **Thème de couleur** Choisissez le thème de couleur **bleu**, **clair** ou **sombre** pour l’IDE.

 Pour installer d’autres thèmes prédéfinis et créer des thèmes personnalisés, téléchargez et installez **l’éditeur de thèmes de couleur de Visual Studio 2015** sur [Visual Studio Marketplace](https://marketplace.visualstudio.com). Une fois cet outil installé, d'autres thèmes de couleurs apparaissent dans la zone de liste des thèmes de couleurs.

 L’option appliquer la casse des titres dans les menus de la barre de menus sont en **majuscules** par défaut dans Visual Studio 2015. Désélectionnez cette option pour les définir sur **Tout en majuscules**.

 **Ajuster automatiquement l’expérience visuelle en fonction des performances du client** Spécifie si Visual Studio définit automatiquement le réglage de l’expérience visuelle ou si vous définissez explicitement l’ajustement. Ce réglage peut changer l'affichage des couleurs, depuis des dégradés jusqu'à des couleurs simples, ou limiter l'utilisation des animations dans les menus ou les fenêtres contextuelles.

 **Activer l’expérience client riche** Active l’expérience visuelle complète de Visual Studio, y compris les dégradés et les animations. Désactivez cette option lors de l’utilisation de connexions Bureau à distance ou de cartes graphiques anciennes, car les performances de ces fonctionnalités peuvent se révéler médiocres dans ces cas. Cette option est disponible seulement quand vous désactivez l’option **Ajuster automatiquement l’expérience visuelle selon les perf. du client**.

 **Utiliser l’accélération graphique matérielle si** elle est disponible Utilise l’accélération graphique matérielle si elle est disponible, plutôt que l’accélération logicielle.

## <a name="other"></a>Autre
 **Éléments affichés dans le menu Fenêtre** Personnalise le nombre de fenêtres qui s’affichent dans la liste Fenêtres du menu **Fenêtre**. Entrez un nombre compris entre 1 et 24. Par défaut, ce nombre est de 10.

 **Éléments affichés dans la liste des fichiers récents** Personnalise le nombre des projets et fichiers utilisés récemment, et qui s’affichent dans le menu **Fichier**. Entrez un nombre compris entre 1 et 24. Par défaut, ce nombre est de 10. Il s'agit d'un moyen facile de récupérer les projets et les fichiers récemment utilisés.

 **Afficher la barre d’état** Affiche la barre d’état. La barre d'état se trouve en bas de la fenêtre de l'IDE et affiche des informations sur la progression des opérations en cours.

 **Le bouton Fermer n’affecte que la fenêtre Outil active** Spécifie qu’au moment où l’utilisateur clique sur le bouton **Fermer**, seule la fenêtre Outil qui a le focus est fermée, et non la totalité des fenêtres Outil de l’ensemble ancré. Cette option est activée par défaut.

 **Le bouton Masquer automatiquement n’affecte que la fenêtre Outil active** Spécifie qu’au moment où l’utilisateur clique sur le bouton **Masquer automatiquement**, seule la fenêtre Outil qui a le focus est masquée automatiquement, et non la totalité des fenêtres Outil de l’ensemble ancré. Cette option est désactivée par défaut.

 **Gérer les associations de fichiers** Affiche la boîte de dialogue **configurer les associations de programmes de Windows** , où vous pouvez afficher les extensions de fichier pour les éléments qui sont généralement associés à Visual Studio et le programme par défaut actuel pour ouvrir chaque type de fichier. Pour faire de Visual Studio l’application par défaut pour les types de fichiers qui n’y sont pas déjà associés, choisissez l’extension de fichier, puis choisissez **Enregistrer**.

 Cette option peut être utile si vous avez deux versions de Visual Studio installées sur le même ordinateur et que vous désinstallez l'une des versions plus tard. Après la désinstallation, les icônes des fichiers Visual Studio n'apparaissent plus dans l'Explorateur de fichiers. En outre, Windows ne reconnaît plus Visual Studio comme application par défaut pour modifier ces fichiers. Cette option restaure ces associations.

## <a name="see-also"></a>Voir aussi
 [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md) [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md)

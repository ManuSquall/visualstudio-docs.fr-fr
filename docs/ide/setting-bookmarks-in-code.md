---
title: Définir des signets de code dans Visual Studio
ms.date: 02/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BookmarkWindow
ms.assetid: a752ed5f-5cf9-4bf2-865a-2131ca600ed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e0154a9d410e7bbe60913b757f216225239704b
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448816"
---
# <a name="set-bookmarks-in-code"></a>Définir des signets dans le code

Vous pouvez utiliser des signets pour marquer des lignes de votre code afin de pouvoir rapidement revenir à un emplacement spécifique, ou basculer d’un emplacement à un autre. Les commandes et les icônes de signet sont disponibles à deux emplacements : dans la fenêtre de signet **Fenêtre Signet** (**Affichage** > **Fenêtre Signet**) et dans la barre d’outils de l’Éditeur de texte.

![Barre d’outils Signet](media/bookmark-toolbar.png)

![Fenêtre Signet](media/bookmark-window.png)

## <a name="manage-bookmarks"></a>Gérer les signets

Pour ajouter un signet, placez le curseur sur la ligne où vous souhaitez insérer un signet. Choisissez le bouton **Activer/désactiver un signet** ou appuyez sur **Ctrl**+**K**, **Ctrl**+**K**. Cela ajoute le signet. Si vous choisissez à nouveau le bouton **Activer/désactiver un signet** (ou si vous appuyez à nouveau sur **Ctrl**+**K**, **Ctrl**+**K**), le signet est supprimé.

Pour voir facilement à quoi est destiné un signet spécifique, vous pouvez le renommer dans la **fenêtre Signet** à partir du menu contextuel obtenu en cliquant avec le bouton droit. Vous pouvez supprimer des signets en choisissant le bouton **Supprimer** de la fenêtre Signet.

> [!IMPORTANT]
> Le signet est défini au numéro de ligne, et non au code. Si vous modifiez le code, le signet est conservé au numéro de ligne ; il ne se déplace pas avec le code.

Vous pouvez naviguer entre les signets à l’aide des boutons **Signet suivant** et **Signet précédent** dans la fenêtre Signet.

Vous pouvez organiser les signets dans des dossiers virtuels en choisissant **Nouveau dossier** dans la fenêtre Signet et en faisant glisser les signets sélectionnés dans le nouveau dossier.

Vous pouvez désactiver les signets (sans les supprimer) en choisissant le bouton **Désactiver tous les signets** dans la fenêtre Signet. Vous pouvez les réactiver en choisissant le même bouton (qui est maintenant libellé **Activer tous les signets**).

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)
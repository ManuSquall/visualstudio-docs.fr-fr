---
title: "Définition de signets dans le code | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.BookmarkWindow
ms.assetid: a752ed5f-5cf9-4bf2-865a-2131ca600ed5
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a7ace58e8cf3a82dce1db789466c55b0e40995c5
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2017
---
# <a name="setting-bookmarks-in-code"></a>Définition de signets dans le code

Vous pouvez utiliser des signets pour marquer les lignes de votre code afin de pouvoir rapidement revenir à un emplacement spécifique et basculer d'un emplacement à un autre. Les commandes et les icônes de signet sont disponibles à deux emplacements : dans la fenêtre de signet (**Affichage** > **Fenêtre Signet**) et dans la barre d’outils de l’Éditeur de texte.

## <a name="managing-bookmarks"></a>Gestion des signets

Pour ajouter un signet, placez le curseur sur la ligne où vous souhaitez insérer un signet. Cliquez sur le bouton **Basculer** ou appuyez sur Ctrl+K. Cela ajoute le signet. Si vous recliquez sur le bouton Basculer (ou si vous réappuyez sur Ctrl+K), le signet est supprimé. Vous pouvez également supprimer des signets en cliquant sur le bouton **Supprimer** dans la fenêtre de signet.

> [!IMPORTANT]
> Le signet est défini au numéro de ligne, et non au code. Si vous modifiez le code, le signet est conservé au numéro de ligne ; il ne se déplace pas avec le code.

Vous pouvez naviguer entre les signets à l’aide des boutons **Signet suivant** et **Signet précédent** dans la fenêtre de signet.

Vous pouvez organiser les signets dans des dossiers virtuels en cliquant sur **Nouveau dossier** dans la fenêtre de signet et en faisant glisser les signets sélectionnés dans le nouveau dossier.

Vous pouvez désactiver des signets (sans les supprimer) en cliquant sur le bouton **Désactiver tous les signets** dans la fenêtre de signet. Vous pouvez les réactiver en cliquant sur le même bouton (qui est maintenant libellé **Activer tous les signets**).

## <a name="see-also"></a>Voir aussi

[Écrire du code dans l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)
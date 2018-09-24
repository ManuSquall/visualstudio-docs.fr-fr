---
title: Guide pratique pour changer le répertoire de sortie de build
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aebb4603d32f61c2d4b50355a550a1a932336962
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379687"
---
# <a name="how-to-change-the-build-output-directory"></a>Guide pratique pour changer le répertoire de sortie de build

Vous pouvez spécifier l’emplacement de sortie en fonction de la configuration (débogage, version ou les deux) généré par votre projet.

> [!NOTE]
> Si vous avez un **projet d’installation**, lisez la remarque à la fin de cet article.

## <a name="change-the-build-output-directory"></a>Changer le répertoire de sortie de build

1.  Dans la barre de menus, choisissez **Projet** > **\<Nom_application> Propriétés**. Vous pouvez également cliquer avec le bouton droit sur le nœud du projet dans **Explorateur de solutions**, puis sélectionner **Propriétés**.

2.  Si vous avez un projet Visual Basic, sélectionnez l'onglet **Compiler** . Si vous avez un projet C#, sélectionnez l'onglet **Générer**. Si vous avez un projet C++ ou un projet JavaScript, sélectionnez l'onglet **Général** .

3.  Dans la liste déroulante de configuration située dans la partie supérieure, choisissez la configuration pour laquelle vous voulez modifier l’emplacement du fichier de sortie (débogage, version ou tout).

     Recherchez l’entrée relative au chemin de sortie (**Chemin de sortie de la génération** en Visual Basic, **Répertoire de sortie** en Visual C++, **Chemin de sortie** en JavaScript et C#). Spécifiez un nouveau répertoire de sortie de génération relatif au répertoire du projet.

> [!NOTE]
> Dans un projet d’installation, la zone **Nom du fichier de sortie** permet uniquement de changer l’emplacement du fichier *Setup.exe*, et non l’emplacement des fichiers projet. Pour plus d’informations, consultez **Build, propriétés de configuration, boîte de dialogue Propriétés du projet de déploiement**.

## <a name="see-also"></a>Voir aussi

- [Générer, page du Concepteur de projets (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Général, page de propriétés (projet)](/cpp/ide/general-property-page-project)
- [Compiler et générer](../ide/compiling-and-building-in-visual-studio.md)
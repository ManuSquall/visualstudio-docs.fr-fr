---
title: Boîte de dialogue Options
description: En savoir plus sur la boîte de dialogue Options, sa disposition et la façon dont Visual Studio applique les options que vous sélectionnez à vos projets et solutions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 79bd2d95a12aa7c42705d106cf71b4061a020431
ms.sourcegitcommit: 113b7df611583307d3965984233a33355d6b0318
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2021
ms.locfileid: "112126539"
---
# <a name="options-dialog-box-visual-studio"></a>Boîte de dialogue Options (Visual Studio)

La boîte de dialogue **Options** vous permet de configurer l’environnement de développement intégré (IDE) selon vos besoins. Par exemple, vous pouvez établir un emplacement d’enregistrement par défaut pour vos projets, modifier l’apparence et le comportement par défaut des fenêtres et créer des raccourcis pour les commandes fréquemment utilisées. Il existe également des options spécifiques à vos plateforme et langage de développement. Vous pouvez accéder aux **Options** à partir du menu **Outils**.

## <a name="layout-of-the-options-dialog-box"></a>Présentation de la boîte de dialogue Options

La boîte de dialogue **Options** est divisée en deux parties : un volet de navigation à gauche et une zone d’affichage à droite. Le contrôle d’arborescence dans le volet de navigation comprend des nœuds de dossier, tels qu’Environnement, Éditeur de texte, Projets et solutions et Contrôle de code source. Développez un nœud de dossier pour afficher les pages d’options qu’il contient. Quand vous sélectionnez le nœud pour une page particulière, ses options apparaissent dans la zone d’affichage.

Les options d’une fonctionnalité IDE n’apparaissent pas dans le volet de navigation tant que cette fonctionnalité n’est pas chargée en mémoire. Ainsi, les options affichées peuvent différer d’une session à l’autre. Quand vous créez un projet ou exécutez une commande qui utilise une application particulière, les nœuds correspondant aux options appropriées sont ajoutés à la boîte de dialogue Options. Ces options ajoutées sont disponibles tant que la fonctionnalité IDE demeure en mémoire.

> [!NOTE]
> Certaines collections de paramètres déterminent la quantité de pages qui s’affichent dans le volet de navigation de la boîte de dialogue Options.

## <a name="how-options-are-applied"></a>Application des options

Cliquer sur OK dans la boîte de dialogue **Options** enregistre tous les paramètres de toutes les pages. Cliquer sur Annuler dans n’importe quelle page annule toutes les demandes de modification, y compris celles effectuées dans les autres pages **Options**. Certaines modifications apportées aux paramètres d’options, telles que celles effectuées dans [Polices et couleurs (section Environnement de la boîte de dialogue Options)](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), ne prennent effet qu’une fois que vous fermez et rouvrez Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Personnalisation de l’éditeur](../how-to-change-text-case-in-the-editor.md)
- [Paramètres et préférences git](../../version-control/git-settings.md)

---
title: Séparer les datasets et les TableAdapters en différents projets
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8a24b934b0ffe4cc22dc7be01aca19910ee3c768
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096866"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Séparer les datasets et les TableAdapters en différents projets
Datasets typés ont été améliorées afin que le [TableAdapters](create-and-configure-tableadapters.md) et classes de jeu de données peuvent être générées dans des projets séparés. Cela vous permet de rapidement séparer les couches application et générer des applications de données multicouches.

La procédure suivante décrit le processus d’utilisation de la **Concepteur de Dataset** pour générer le code de jeu de données dans un projet qui est séparé du projet qui contient le code du TableAdapter généré.

## <a name="separate-datasets-and-tableadapters"></a>Séparer les datasets et des TableAdapters
Lorsque vous séparez le code de jeu de données à partir de code du TableAdapter, le projet qui contient le code de jeu de données doit se trouver dans la solution actuelle. Si ce projet ne se trouve pas dans la solution actuelle, il n’est pas disponible dans le **DataSet Project** liste dans le **propriétés** fenêtre.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Pour séparer le jeu de données dans un autre projet

1. Ouvrez une solution qui contient un jeu de données (*.xsd* fichier).

    > [!NOTE]
    >  Si la solution ne contient pas le projet dans lequel vous souhaitez séparer le code de votre jeu de données, créer le projet, ou ajouter un projet existant à la solution.

2. Double-cliquez sur un fichier de dataset typé (une *.xsd* fichier) dans **l’Explorateur de solutions** pour ouvrir le jeu de données dans le **Concepteur de Dataset**.

3. Sélectionnez une zone vide de la **Concepteur de Dataset**.

4. Dans le **propriétés** fenêtre, recherchez le **DataSet Project** nœud.

5. Dans le **DataSet Project** liste, sélectionnez le nom du projet dans lequel vous souhaitez générer le code de jeu de données.

     Après avoir sélectionné le projet dans lequel vous souhaitez générer le code de jeu de données, le **fichier DataSet** propriété est remplie avec un nom de fichier par défaut. Vous pouvez modifier ce nom si nécessaire. En outre, si vous souhaitez générer le code de jeu de données dans un répertoire spécifique, vous pouvez définir le **dossier du projet** propriété le nom d’un dossier.

    > [!NOTE]
    >  Quand vous séparez les datasets et les TableAdapters (en définissant le **DataSet Project** propriété), les classes dataset partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes dataset partielles existantes doivent être déplacés manuellement dans le projet dataset.

6. Enregistrer le jeu de données.

     Le code de jeu de données est généré dans le projet sélectionné dans le **DataSet Project** propriété et le **TableAdapter** code est généré dans le projet actuel.

Par défaut, une fois que vous séparez le jeu de données et le code du TableAdapter, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé *NomGroupeDonnées.Designer.vb* (ou *NomGroupeDonnées.Designer.cs*) qui contient le code du TableAdapter. Le projet désigné dans la **Dataset Project** propriété dispose d’un fichier nommé *NomGroupeDonnées.DataSet.Designer.vb* (ou *NomGroupeDonnées.DataSet.Designer.cs*) qui contient le code de jeu de données.

> [!NOTE]
>  Pour afficher le fichier de classe générée, sélectionnez le jeu de données ou le projet de TableAdapter. Ensuite, dans **l’Explorateur de solutions**, sélectionnez **afficher tous les fichiers**.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des applications de données multiniveaux](../data-tools/n-tier-data-applications-overview.md)
- [Procédure pas à pas : Création d’une application de données multiniveaux](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)
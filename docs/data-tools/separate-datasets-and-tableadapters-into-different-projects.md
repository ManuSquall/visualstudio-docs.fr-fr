---
title: Séparer les datasets et les TableAdapters en différents projets
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8df444646512ecd4dba866fccf6da5fdf7a8bab3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586222"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Séparer les datasets et les TableAdapters en différents projets
Les datasets typés ont été améliorés afin que les classes de datasets et de [TableAdapters](create-and-configure-tableadapters.md) puissent être générées dans des projets distincts. Cela vous permet de séparer rapidement les couches d’application et de générer des applications de données multicouches.

La procédure suivante décrit le processus d’utilisation de l' **Concepteur de DataSet** pour générer du code de DataSet dans un projet distinct du projet qui contient le code du TableAdapter généré.

## <a name="separate-datasets-and-tableadapters"></a>DataSets et TableAdapters séparés
Lorsque vous séparez le code d’un DataSet du code du TableAdapter, le projet qui contient le code du DataSet doit se trouver dans la solution actuelle. Si ce projet n’est pas situé dans la solution actuelle, il ne sera pas disponible dans la liste **projet de DataSet** de la fenêtre **Propriétés** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Pour séparer le DataSet dans un autre projet

1. Ouvrez une solution qui contient un jeu de données (fichier *. xsd* ).

    > [!NOTE]
    > Si la solution ne contient pas le projet dans lequel vous souhaitez séparer le code de votre jeu de données, créez le projet ou ajoutez un projet existant à la solution.

2. Double-cliquez sur un fichier de DataSet typé (un fichier *. xsd* ) dans **Explorateur de solutions** pour ouvrir le jeu de données dans le **Concepteur de DataSet**.

3. Sélectionnez une zone vide du **Concepteur de DataSet**.

4. Dans la fenêtre **Propriétés** , recherchez le nœud de **projet DataSet** .

5. Dans la liste **projet de DataSet** , sélectionnez le nom du projet dans lequel vous souhaitez générer le code du DataSet.

     Une fois que vous avez sélectionné le projet dans lequel vous souhaitez générer le code du jeu de données, la propriété **fichier du DataSet** est remplie avec un nom de fichier par défaut. Vous pouvez modifier ce nom si nécessaire. En outre, si vous souhaitez générer le code du DataSet dans un répertoire spécifique, vous pouvez définir la propriété **dossier du projet** sur le nom d’un dossier.

    > [!NOTE]
    > Lorsque vous séparez des DataSets et des TableAdapters (en définissant la propriété **DataSet Project** ), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes de DataSet partielles existantes doivent être déplacées manuellement vers le projet de DataSet.

6. Enregistrez le jeu de données.

     Le code du DataSet est généré dans le projet sélectionné dans la propriété **DataSet Project** et le code du **TableAdapter** est généré dans le projet actuel.

Par défaut, après avoir séparé le jeu de données et le code du TableAdapter, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé *NomGroupeDonnées. Designer. vb* (ou *DataSetName.Designer.cs*) qui contient le code du TableAdapter. Le projet désigné dans la propriété de **projet DataSet** a un fichier nommé *NomGroupeDonnées. DataSet. Designer. vb* (ou *DataSetName.DataSet.Designer.cs*) qui contient le code du DataSet.

> [!NOTE]
> Pour afficher le fichier de classe généré, sélectionnez le DataSet ou le projet TableAdapter. Ensuite, dans **Explorateur de solutions**, sélectionnez **Afficher tous les fichiers**.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des applications de données multiniveaux](../data-tools/n-tier-data-applications-overview.md)
- [Procédure pas à pas : Création d’une application de données multiniveau](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)

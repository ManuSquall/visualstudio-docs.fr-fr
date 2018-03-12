---
title: "Séparer des datasets et les TableAdapters dans différents projets | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: af4e082bfa3e1b7669eb43218977b03a47c2f0bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Jeux de données distincts et les TableAdapters dans différents projets
Datasets typés ont été améliorés afin que les [TableAdapters](create-and-configure-tableadapters.md) et les classes dataset puissent être générées dans des projets distincts. Cela vous permet de rapidement séparer les couches d’application et de générer des applications de données multicouches.  
  
La procédure suivante décrit le processus de l’utilisation de la **Concepteur de Dataset** pour générer le code de jeu de données dans un projet qui est séparé du projet qui contient le code du TableAdapter généré.  
  
## <a name="separate-datasets-and-tableadapters"></a>Jeux de données distincts et les TableAdapters  
Lorsque vous séparez le code du jeu de données à partir du code du TableAdapter, le projet qui contient le code du jeu de données doit se trouver dans la solution actuelle. Si ce projet ne se trouve pas dans la solution actuelle, il n’est pas disponible dans le **projet DataSet** liste dans le **propriétés** fenêtre.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Pour séparer le jeu de données dans un autre projet  
  
1.  Ouvrez une solution qui contient un jeu de données (fichier .xsd).  
  
    > [!NOTE]
    >  Si la solution ne contient pas le projet dans lequel vous souhaitez séparer le code de votre jeu de données, créer le projet, ou ajouter un projet existant à la solution.  
  
2.  Double-cliquez sur un fichier dataset typé (fichier .xsd) dans **l’Explorateur de solutions** pour ouvrir le dataset dans le **Concepteur de Dataset**.  
  
3.  Sélectionnez une zone vide de la **Concepteur de Dataset**.  
  
4.  Dans le **propriétés** fenêtre, recherchez le **projet DataSet** nœud.  
  
5.  Dans le **projet DataSet** , sélectionnez le nom du projet dans lequel vous souhaitez générer le code de jeu de données.  
  
     Après avoir sélectionné le projet dans lequel vous souhaitez générer le code de jeu de données, le **fichier DataSet** propriété est remplie avec un nom de fichier par défaut. Vous pouvez modifier ce nom si nécessaire. En outre, si vous souhaitez générer le code de jeu de données dans un répertoire spécifique, vous pouvez définir le **dossier du projet** nom à la propriété d’un dossier.  
  
    > [!NOTE]
    >  Quand vous séparez les datasets et les TableAdapters (en définissant le **projet DataSet** propriété), les classes dataset partielles existantes dans le projet ne sera pas être déplacées automatiquement. Les classes dataset partielles existantes doivent être déplacés manuellement vers le projet dataset.  
  
6.  Enregistrer le jeu de données.  
  
     Le code de jeu de données est généré dans le projet sélectionné dans le **projet DataSet** propriété et le **TableAdapter** code est généré dans le projet actuel.  
  
Par défaut, une fois que vous séparez le dataset et le code du TableAdapter, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé NomGroupeDonnées.Designer.vb (ou NomGroupeDonnées.Designer.cs) qui contient le code du TableAdapter. Le projet désigné dans la **projet Dataset** propriété dispose d’un fichier nommé NomGroupeDonnées.DataSet.Designer.vb (ou NomGroupeDonnées.DataSet.Designer.cs) qui contient le code du jeu de données.  
  
> [!NOTE]
>  Pour afficher le fichier de classe générée, sélectionnez le jeu de données ou le projet de TableAdapter. Ensuite, dans **l’Explorateur de solutions**, sélectionnez **afficher tous les fichiers**.  
  
## <a name="see-also"></a>Voir aussi
[Vue d’ensemble des Applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)   
[Procédure pas à pas : Création d’une Application de données multicouche](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
[Mise à jour hiérarchique](../data-tools/hierarchical-update.md)   
[Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
[ADO.NET](/dotnet/framework/data/adonet/index)
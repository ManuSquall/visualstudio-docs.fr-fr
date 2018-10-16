---
title: Séparer les datasets et les TableAdapters dans différents projets | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cca40c194db476558ff14b5c92a6919c15d204a2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272400"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Séparer les datasets et les TableAdapters en différents projets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Datasets typés ont été améliorées afin que le [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) et classes de jeu de données peuvent être générées dans des projets séparés. Cela vous permet de rapidement séparer les couches application et générer des applications de données multicouches.  
  
 La procédure suivante décrit le processus d’utilisation de la[création et modification de données typés](../data-tools/creating-and-editing-typed-datasets.md) pour générer le code de jeu de données dans un projet qui est séparé du projet qui contient le texte généré `TableAdapter` code.  
  
## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets et les TableAdapters  
 Quand vous séparez le code de jeu de données à partir de `TableAdapter` code, le projet qui contient le code de jeu de données doit se trouver dans la solution actuelle. Si ce projet ne se trouve pas dans la solution actuelle, il n’est pas disponible dans le **DataSet Project** liste dans le **propriétés** fenêtre.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Pour séparer le jeu de données dans un autre projet  
  
1.  Ouvrez une solution qui contient un jeu de données (fichier .xsd).  
  
    > [!NOTE]
    >  Si la solution ne contient pas le projet dans lequel vous souhaitez séparer le code de votre jeu de données, créer le projet, ou ajouter un projet existant à la solution.  
  
2.  Double-cliquez sur un fichier de dataset typé (fichier .xsd) dans **l’Explorateur de solutions** pour ouvrir le jeu de données dans le **Concepteur de Dataset**.  
  
3.  Sélectionnez une zone vide de la **Concepteur de Dataset**.  
  
4.  Dans le **propriétés** fenêtre, recherchez le **DataSet Project** nœud.  
  
5.  Dans le **DataSet Project** liste, sélectionnez le nom du projet dans lequel vous souhaitez générer le code de jeu de données.  
  
     Après avoir sélectionné le projet dans lequel vous souhaitez générer le code de jeu de données, le **fichier DataSet** propriété est remplie avec un nom de fichier par défaut. Vous pouvez modifier ce nom si nécessaire. En outre, si vous souhaitez générer le code de jeu de données dans un répertoire spécifique, vous pouvez définir le **dossier du projet** propriété le nom d’un dossier.  
  
    > [!NOTE]
    >  Quand vous séparez les datasets et les TableAdapters (en définissant le **DataSet Project** propriété), les classes dataset partielles existantes dans le projet ne sont pas déplacées automatiquement. Classes dataset partielles existantes doivent être déplacés manuellement vers le projet dataset.  
  
6.  Enregistrer le jeu de données.  
  
     Le code de jeu de données est généré dans le projet sélectionné dans le **DataSet Project** propriété et le **TableAdapter** code est généré dans le projet actuel.  
  
 Par défaut, une fois que vous séparez le dataset et `TableAdapter` code, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé NomGroupeDonnées.Designer.vb (ou NomGroupeDonnées.Designer.cs) qui contient le `TableAdapter` code. Le projet désigné dans la **Dataset Project** propriété dispose d’un fichier nommé NomGroupeDonnées.DataSet.Designer.vb (ou NomGroupeDonnées.DataSet.Designer.cs) qui contient le code de jeu de données.  
  
> [!NOTE]
>  Pour afficher le fichier de classe générée, sélectionnez le jeu de données ou `TableAdapter` projet. Ensuite, dans **l’Explorateur de solutions**, sélectionnez **afficher tous les fichiers** .  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des Applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)   
 [Procédure pas à pas : Création d’une Application de données multicouches](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)   
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)


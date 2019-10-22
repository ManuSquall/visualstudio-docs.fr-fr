---
title: Séparer des DataSets et des TableAdapters dans différents projets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f6ec76e79cc1c4759cbe05d8bdcacc1297b655b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655436"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Séparer les datasets et les TableAdapters en différents projets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les datasets typés ont été améliorés afin que les classes de datasets et de [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) puissent être générées dans des projets distincts. Cela vous permet de séparer rapidement les couches d’application et de générer des applications de données multicouches.

 La procédure suivante décrit le processus d’utilisation de l’Concepteur de DataSet pour générer du code de jeu de données dans un projet distinct du projet qui contient le code de `TableAdapter` généré.

## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets et TableAdapters
 Lorsque vous séparez le code d’un DataSet du code `TableAdapter`, le projet qui contient le code du DataSet doit se trouver dans la solution actuelle. Si ce projet n’est pas situé dans la solution actuelle, il ne sera pas disponible dans la liste **projet de DataSet** de la fenêtre **Propriétés** .

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Pour séparer le DataSet dans un autre projet

1. Ouvrez une solution qui contient un jeu de données (fichier. xsd).

   > [!NOTE]
   > Si la solution ne contient pas le projet dans lequel vous souhaitez séparer le code de votre jeu de données, créez le projet ou ajoutez un projet existant à la solution.

2. Double-cliquez sur un fichier de DataSet typé (un fichier. xsd) dans **Explorateur de solutions** pour ouvrir le jeu de données dans le **Concepteur de DataSet**.

3. Sélectionnez une zone vide du **Concepteur de DataSet**.

4. Dans la fenêtre **Propriétés** , recherchez le nœud de **projet DataSet** .

5. Dans la liste **projet de DataSet** , sélectionnez le nom du projet dans lequel vous souhaitez générer le code du DataSet.

    Une fois que vous avez sélectionné le projet dans lequel vous souhaitez générer le code du jeu de données, la propriété **fichier du DataSet** est remplie avec un nom de fichier par défaut. Vous pouvez modifier ce nom si nécessaire. En outre, si vous souhaitez générer le code du DataSet dans un répertoire spécifique, vous pouvez définir la propriété **dossier du projet** sur le nom d’un dossier.

   > [!NOTE]
   > Lorsque vous séparez des DataSets et des TableAdapters (en définissant la propriété **DataSet Project** ), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes partielles de DataSet existantes doivent être déplacées manuellement vers le projet de DataSet.

6. Enregistrez le jeu de données.

    Le code du DataSet est généré dans le projet sélectionné dans la propriété **DataSet Project** et le code du **TableAdapter** est généré dans le projet actuel.

   Par défaut, après avoir séparé le jeu de données et `TableAdapter` code, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé NomGroupeDonnées. Designer. vb (ou DatasetName.Designer.cs) qui contient le code `TableAdapter`. Le projet désigné dans la propriété de **projet DataSet** a un fichier nommé NomGroupeDonnées. DataSet. Designer. vb (ou DataSetName.DataSet.Designer.cs) qui contient le code du DataSet.

> [!NOTE]
> Pour afficher le fichier de classe généré, sélectionnez le jeu de données ou le projet de `TableAdapter`. Ensuite, dans **Explorateur de solutions**, sélectionnez **Afficher tous les fichiers** .

## <a name="see-also"></a>Voir aussi
 [Présentation des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md) [procédure pas à pas : création d’une](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [mise à jour hiérarchique](../data-tools/hierarchical-update.md) d’application de données multicouche [accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [ADO.net](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)

---
title: 'Comment : ajouter des requêtes globales à un TableAdapter | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- global functions, datasets
- scalar functions, datasets
- TableAdapters, global queries
- data [Visual Studio], TableAdapters
- datasets [Visual Basic], scalar functions
- TableAdapter Query Configuration Wizard
- datasets [Visual Basic], global functions
- TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 681fea494557e555c745d33c07c4e2c25cfe0f88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496200"
---
# <a name="how-to-add-global-queries-to-a-tableadapter"></a>Comment : ajouter des requêtes globales à un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Requêtes globales* sont des requêtes SQL qui retournent une valeur (scalaire) unique ou aucune valeur. En règle générale, les fonctions globales effectuent des opérations de base de données telles que des insertions, mises à jour, suppressions et le regroupement d’informations, par exemple le nombre de clients dans une table ou le total des frais pour tous les éléments dans un ordre particulier.  
  
 Vous ajoutez des requêtes globales en exécutant la **Assistant Configuration de requêtes TableAdapter** depuis le **Concepteur de Dataset**.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-global-query-to-a-dataset"></a>Pour ajouter une requête globale à un jeu de données  
  
1.  Ouvrez un dataset dans le **Concepteur de Dataset**. Pour plus d’informations, consultez [Comment : ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Faites glisser un **requête** à partir de la **DataSet** onglet de la **boîte à outils** dans une zone vide de la **Concepteur de Dataset**.  
  
     Le [modification des TableAdapters](../data-tools/editing-tableadapters.md) s’ouvre.  
  
3.  Choisir une connexion pour la requête à utiliser. Vous pouvez choisir un dans la liste ou créez une nouvelle connexion. Si vous créez une nouvelle connexion, avoir l’option à l’enregistrer dans le fichier de configuration d’application. Pour plus d’informations, consultez [Comment : enregistrer et modifier des chaînes de connexion](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
4.  Choisissez s’il faut utiliser des instructions SQL ou des procédures stockées.  
  
5.  Choisissez la procédure stockée à utiliser ou, dans le **choisir un Type de requête** page de l’Assistant, choisissez le type de requête souhaité, puis cliquez sur **suivant**.  
  
6.  Fournir une requête qui effectue la tâche souhaitée, par exemple, `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Déplacement d’une requête directement sur le **Concepteur de Dataset** crée une méthode qui retourne uniquement une valeur scalaire (unique). Pendant la requête ou la procédure stockée que vous sélectionnez peut retourner plus de valeur unique, la méthode créée par l’Assistant retourne uniquement une valeur unique. Par exemple, la requête peut retourner la première colonne de la première ligne des données retournées.  
  
7.  Terminez l’Assistant ; la requête est ajoutée à la **Concepteur de Dataset**. Pour plus d’informations sur l’exécution de la requête, consultez [Comment : exécuter des requêtes TableAdapter](http://msdn.microsoft.com/library/c7518855-f896-41c1-b3de-1a8116280593).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)   
 [Comment : établir une connexion à des données d’une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)
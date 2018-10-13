---
title: 'Comment : démarrer l’Assistant Configuration de TableAdapter | Microsoft Docs'
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
- TableAdapters, Configuration Wizard
- TableAdapter Configuration Wizard
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7f603789014239762f564c3b2391b99865d8f620
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261889"
---
# <a name="how-to-start-the-tableadapter-configuration-wizard"></a>Comment : démarrer l'Assistant Configuration de TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le **Assistant Configuration de TableAdapter** crée et modifie des TableAdapters dans les datasets fortement typés. L'Assistant crée des TableAdapters basés sur des instructions SQL que vous entrez dans l'Assistant ou sur des procédures stockées existantes dans la base de données. L'Assistant peut également créer des procédures stockées dans la base de données en fonction des instructions SQL que vous y entrez.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-create-a-new-tableadapter"></a>Pour démarrer l'Assistant Configuration de TableAdapter afin de créer un TableAdapter  
  
1.  Ouvrez votre jeu de données dans le **Concepteur de Dataset**. Pour plus d’informations, consultez [Comment : ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
    > [!NOTE]
    >  Si vous n’avez pas d’un jeu de données dans votre projet, consultez [créer et configurer des datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Si vous créez un nouveau TableAdapter, faites glisser un **TableAdapter** de l’objet à partir de la **DataSet** onglet de la **boîte à outils** sur le **Concepteur de Dataset**.  
  
3.  Sur le **choisir votre connexion de données** page, sélectionnez une connexion de données dans la liste des connexions actuellement disponibles ou sélectionnez **nouvelle connexion** pour créer une nouvelle connexion.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-edit-an-existing-tableadapter"></a>Pour démarrer l'Assistant Configuration de TableAdapter afin de modifier un TableAdapter existant  
  
1.  Ouvrez votre jeu de données dans le **Concepteur de Dataset**. Pour plus d’informations, consultez [Comment : ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Cliquez sur le TableAdapter dans le **Concepteur de Dataset** et choisissez **configurer**. L’Assistant s’ouvre à la **générer les instructions SQL** page ou le **lier des commandes à des procédures stockées existantes** page, selon la configuration à l’origine du TableAdapter.  
  
3.  Effectuez toutes les étapes de l'Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)   
 [Comment : établir une connexion à des données d’une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Comment : trier et filtrer des données ADO.NET avec le composant de BindingSource Windows Forms](http://msdn.microsoft.com/library/6c206daf-d706-4602-9dbe-435343052063)   
 [Comment : créer une Table de correspondance avec le composant de BindingSource Windows Forms](http://msdn.microsoft.com/library/622fce80-879d-44be-abbf-8350ec22ca2b)   
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)
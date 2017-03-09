---
title: "Comment&#160;: ajouter des requ&#234;tes globales &#224; un groupe de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), TableAdapters"
  - "groupes de données (Visual Basic), fonctions globales"
  - "groupes de données (Visual Basic), fonctions scalaires"
  - "fonctions globales, groupes de données"
  - "requêtes (Visual Studio), TableAdapters"
  - "fonctions scalaires, groupes de données"
  - "requêtes TableAdapter"
  - "Configuration de requête TableAdapter (Assistant)"
  - "TableAdapters, requêtes globales"
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: ajouter des requ&#234;tes globales &#224; un groupe de donn&#233;es
Les *requêtes globales* sont des requêtes SQL qui retournent une valeur unique \(scalaire\) ou aucune valeur.  En général, les fonctions globales exécutent des opérations de base de données telles que les insertions, les mises à jour, les suppressions et le regroupement d'informations \(par exemple le nombre de clients contenus dans une table ou les charges totales de tous les éléments d'une commande particulière\).  
  
 Vous pouvez ajouter des requêtes globales en exécutant l'**Assistant Configuration de requêtes TableAdapter** à partir du **Concepteur de DataSet**.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Pour ajouter une requête globale à un groupe de données  
  
1.  Ouvrez un groupe de données dans le **Concepteur de DataSet**.  Pour plus d'informations, consultez [Comment : ouvrir un groupe de données dans le Concepteur de DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Faites glisser une **Requête** depuis l'onglet **DataSet** de la **Boîte à outils** jusqu'à une zone vide du **Concepteur de DataSet**.  
  
     La [Configuration de requête TableAdapter \(Assistant\)](../data-tools/editing-tableadapters.md) s'ouvre.  
  
3.  Choisissez une connexion pour la requête à utiliser.  Vous pouvez sélectionner une connexion dans la liste ou en créer une nouvelle.  Si vous créez une nouvelle connexion, vous pouvez choisir de l'enregistrer dans le fichier de configuration de l'application.  Pour plus d'informations, consultez [Comment : enregistrer et modifier des chaînes de connexion](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
4.  Choisissez s'il convient d'utiliser des instructions SQL ou des procédures stockées.  
  
5.  Choisissez la procédure stockée à utiliser ou, sur la page **Choisir un type de requête** de l'Assistant, choisissez le type de requête souhaité, puis cliquez sur **Suivant**.  
  
6.  Spécifiez une requête qui exécute la tâche souhaitée \(par exemple, `SELECT COUNT(*) AS CustomerCount FROM Customers`\).  
  
    > [!NOTE]
    >  Si vous faites glisser directement une requête jusqu'au **Concepteur de DataSet**, une méthode qui ne retournera qu'une valeur scalaire \(unique\) est créée.  Alors que la requête ou la procédure stockée que vous sélectionnez peut retourner plusieurs valeurs, la méthode créée par l'Assistant ne renvoie qu'une seule valeur.  Par exemple, la requête peut retourner la première colonne de la première ligne des données retournées.  
  
7.  Une fois l'Assistant terminé, la requête est ajoutée au **Concepteur de DataSet**.  Pour plus d'informations sur l'exécution de la requête, consultez [Comment : exécuter des requêtes TableAdapter](../Topic/How%20to:%20Execute%20TableAdapter%20Queries.md).  
  
## Voir aussi  
 [Comment : créer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Comment : établir une connexion à des données d'une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)
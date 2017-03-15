---
title: "Mise &#224; jour hi&#233;rarchique | Microsoft Docs"
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
  - "données (Visual Basic), mise à jour hiérarchique"
  - "groupes de données (Visual Basic), mise à jour hiérarchique"
  - "mise à jour hiérarchique"
  - "enregistrement des données modifiées"
  - "tables connexes, enregistrer"
  - "enregistrer les données, données modifiées"
  - "enregistrer les données, mise à jour hiérarchique"
  - "enregistrer les données mises à jour"
  - "enregistrement des données mises à jour"
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 26
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mise &#224; jour hi&#233;rarchique
La *mise à jour hiérarchique* fait référence au processus d'enregistrement des données mises à jour \(d'un groupe de données avec au moins deux tables connexes\) dans une base de données en maintenant des règles d'intégrité référentielle.  L'*intégrité référentielle* fait référence aux règles de cohérence fournies par les contraintes dans une base de données qui contrôlent le comportement des enregistrements connexes d'insertion, de mise à jour et de suppression.  Par exemple, l'intégrité référentielle impose la création d'un enregistrement de client avant d'autoriser la création de commandes pour ce client.  
  
 L'enregistrement des données modifiées des tables de données connexes est une opération un peu plus complexe que l'enregistrement des données d'une table individuelle.  Les commandes INSERT, UPDATE et DELETE pour chaque table connexe doivent être exécutées dans un ordre spécifique pour éviter de violer les contraintes d'intégrité référentielle.  Prenons l'exemple d'une application d'enregistrement de commandes avec laquelle vous pouvez gérer à la fois les commandes et les clients nouveaux et existants.  Si vous devez supprimer un client existant, vous devez tout d'abord supprimer tous les commandes de ce client avant de supprimer l'enregistrement du client.  Si vous ajoutez un nouveau client \(avec une commande\), vous devez tout d'abord insérer le nouvel enregistrement de client avant d'insérer les commandes de ce client à cause des contraintes de clé étrangère qui sont dans les tables.  Ces exemples montrent que vous devez extraire des sous\-ensembles spécifiques de données et envoyer les mises à jour \(insertions, mises à jour et suppressions\) dans l'ordre approprié pour maintenir l'intégrité référentielle.  
  
 La fonctionnalité de mise à jour hiérarchique utilise un `TableAdapterManager` pour gérer les `TableAdapter`s dans un groupe de données typé.  Le composant `TableAdapterManager` est un composant généré par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il ne fait donc pas partie du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Pour plus d'informations sur la classe `TableAdapterManager`, consultez la section de référence de TableAdapterManager de la [Vue d'ensemble de TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
 Si votre application utilise des groupes de données typés et permet aux utilisateurs de modifier les données dans des tables de données connexes \(tables de données avec une relation de type un\-à\-plusieurs telles que Customers et Orders\), vous souhaiterez probablement utiliser la mise à jour hiérarchique.  
  
## Dans cette section  
 [Vue d'ensemble de la mise à jour hiérarchique](../Topic/Hierarchical%20Update%20Overview.md)  
 Décrit la mise à jour hiérarchique et fournit des informations détaillées sur son implémentation.  
  
 [Vue d'ensemble de TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)  
 Décrit un `TableAdapterManager` et fournit des descriptions du code `TableAdapterManager` généré par le Concepteur de DataSet.  
  
 [Comment : activer et désactiver la mise à jour hiérarchique](../Topic/How%20to:%20Enable%20and%20Disable%20Hierarchical%20Update.md)  
 Décrit comment définir la propriété `Hierarchical Update` d'un groupe de données typé pour générer le code afin d'enregistrer des tables connexes.  
  
 [Comment : configurer des contraintes de clé étrangère dans un groupe de données](../Topic/How%20to:%20Configure%20Foreign-Key%20Constraints%20in%20a%20Dataset.md)  
 Décrit comment configurer les contraintes dans un groupe de données.  
  
 [Comment : valider des modifications in\-process sur des contrôles liés aux données avant d'enregistrer des données](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
 Décrit comment arrêter toutes les modifications in\-process dans les contrôles liés aux données sur un formulaire pour préparer la source de données avant de l'enregistrer.  
  
 [Comment : définir l'ordre lors de l'exécution d'une mise à jour hiérarchique](../Topic/How%20to:%20Set%20the%20Order%20When%20Performing%20a%20Hierarchical%20Update.md)  
 Décrit comment définir la propriété `UpdateOrder` d'un `TableAdapterManager` pour contrôler l'ordre dans lequel les commandes INSERT, UPDATE et DELETE sont exécutées.  
  
 [Comment : implémenter une mise à jour hiérarchique dans des projets Visual Studio existants](../Topic/How%20to:%20Implement%20Hierarchical%20Update%20in%20Existing%20Visual%20Studio%20Projects.md)  
 Décrit comment mettre à niveau une application qui a des tables de données connexes pour enregistrer des données à l'aide de `TableAdapterManager`.  
  
 [Procédure pas à pas : enregistrement des données de tables de données connexes \(Mise à jour hiérarchique\)](../Topic/Walkthrough:%20Saving%20Data%20from%20Related%20Data%20Tables%20\(Hierarchical%20Update\).md)  
 Fournit des instructions pas à pas pour créer une application qui a des tables de données connexes et enregistrer les données à l'aide de `TableAdapterManager`.  
  
## Référence  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.DataTable>  
  
## Rubriques connexes  
 [Utilisation de groupes de données dans des applications multicouches](../data-tools/work-with-datasets-in-n-tier-applications.md)  
  
 [Enregistrement des données](../data-tools/saving-data.md)  
  
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)  
  
 [TableAdapters](../Topic/TableAdapters.md)  
  
 [Objets DataSet, DataTable et DataView](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)  
  
 [DataTable, objets](../Topic/DataTables.md)  
  
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
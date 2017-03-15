---
title: "Proc&#233;dure&#160;: examiner le mod&#232;le de contenu de nœuds &#224; l&#39;aide de la vue de mod&#232;le de contenu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: examiner le mod&#232;le de contenu de nœuds &#224; l&#39;aide de la vue de mod&#232;le de contenu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit comment explorer vos nœuds à l'aide de la [Vue de modèle de contenu](../xml-tools/content-model-view.md).  
  
### Pour créer un fichier XSD et afficher l'élément racine dans la vue de modèle de contenu  
  
1.  Créez un fichier de schéma XML.  
  
2.  Cliquez sur **Utiliser l'Éditeur XML pour afficher et modifier le fichier de schéma XML sous\-jacent** dans la vue de départ.  
  
3.  Copiez le code de l'exemple de schéma XML à partir de [Exemple de schéma XML : schéma de bon de commande](../Topic/Sample%20XSD%20File:%20Purchase%20Order%20Schema.md), puis collez\-le pour remplacer le code qui a été ajouté par défaut au nouveau fichier XSD.  
  
4.  Sélectionnez l'élément `purchaseOrder` dans l'Explorateur de schémas en cliquant avec le bouton droit sur l'élément `purchaseOrder` dans l'Éditeur XML et en sélectionnant **Afficher dans l'Explorateur XML**.  
  
5.  Cliquez avec le bouton droit sur le `purchaseOrder` dans l'Explorateur XML, puis sélectionnez **Afficher la vue de modèle de contenu**.  
  
     La vue de modèle de contenu affiche l'élément `purchaseOrder` sur son aire de conception.  
  
6.  Développez les nœuds`shipTo`, `billTo` et `items` en double\-cliquant sur chaque nœud ou en cliquant sur la flèche double à droite de chaque nœud.  
  
     Les nœuds de l'élément `purchaseOrder` sont maintenant développés et vous pouvez consulter le modèle de contenu de l'élément.  
  
7.  Cliquez sur n'importe quel nœud sous l'élément `purchaseOrder`, puis examinez la barre de fil d'Ariane \(breadcrumb\) pour déterminer l'emplacement du nœud sélectionné dans le jeu de schémas.  
  
8.  Cliquez sur le bouton **Afficher la documentation** dans la barre d'outils XSD pour basculer vers la documentation.Vous pouvez également cliquer avec le bouton droit sur l'aire de conception pour basculer vers la documentation.  
  
9. Cliquez avec le bouton droit sur le nœud `purchaseOrder`, puis sélectionnez **Générer un exemple de code XML** pour consulter le document de l'instance XML.
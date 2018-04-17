---
title: 'Comment : examiner le modèle de contenu de nœuds à l’aide de la vue de modèle de contenu | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4b2430cd90a63d02503a99e26c893a3f59a5246
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Procédure : examiner le modèle de contenu de nœuds à l'aide de la vue de modèle de contenu
Cette rubrique explique comment Explorer vos nœuds à l’aide de la [affichage du modèle de contenu](../xml-tools/content-model-view.md).  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Pour créer un fichier XSD et afficher l'élément racine dans la vue de modèle de contenu  
  
1.  Créez un fichier de schéma XML.  
  
2.  Cliquez sur **utiliser l’éditeur XML pour afficher et modifier le fichier de schéma XML sous-jacent** sur la vue de départ.  
  
3.  Copiez le code d’exemple de schéma XML à partir de [exemple de schéma XML : schéma de bon de commande](../xml-tools/sample-xsd-file-purchase-order-schema.md) et collez-le pour remplacer le code qui a été ajouté au nouveau fichier XSD par défaut.  
  
4.  Sélectionnez le `purchaseOrder` élément dans l’Explorateur de schémas en cliquant sur le `purchaseOrder` élément dans l’éditeur XML et en sélectionnant **afficher dans l’Explorateur XML**.  
  
5.  Cliquez sur le `purchaseOrder` dans l’Explorateur de XML et sélectionnez **afficher en vue de modèle de contenu**.  
  
     La vue de modèle de contenu affiche l'élément `purchaseOrder` sur son aire de conception.  
  
6.  Développez les nœuds`shipTo`, `billTo` et `items` en double-cliquant sur chaque nœud ou en cliquant sur la flèche double à droite de chaque nœud.  
  
     Les nœuds de l'élément `purchaseOrder` sont maintenant développés et vous pouvez consulter le modèle de contenu de l'élément.  
  
7.  Cliquez sur n'importe quel nœud sous l'élément `purchaseOrder`, puis examinez la barre de fil d'Ariane (breadcrumb) pour déterminer l'emplacement du nœud sélectionné dans le jeu de schémas.  
  
8.  Cliquez sur le **afficher la Documentation** bouton dans la barre d’outils XSD pour basculer vers la documentation. Vous pouvez également cliquer avec le bouton droit sur l'aire de conception pour basculer vers la documentation.  
  
9. Cliquez le `purchaseOrder` nœud et sélectionnez **générer un exemple XML** pour consulter le document d’instance XML.
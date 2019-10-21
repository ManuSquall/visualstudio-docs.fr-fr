---
title: 'Comment : examiner le modèle de contenu des nœuds à l’aide de la vue de modèle de contenu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ddadcb0fbd772a5638bf6023b8cf6c18fbd270d7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670857"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Procédure : examiner le modèle de contenu de nœuds à l'aide de la vue de modèle de contenu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique explique comment explorer vos nœuds à l’aide de la [vue de modèle de contenu](../xml-tools/content-model-view.md).

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Pour créer un fichier XSD et afficher l'élément racine dans la vue de modèle de contenu

1. Créez un fichier de schéma XML.

2. Cliquez sur **utiliser l’éditeur XML pour afficher et modifier le fichier de schéma XML sous-jacent** dans la vue de départ.

3. Copiez l’exemple de code XML à partir de exemple de schéma [XML : schéma de bon de commande](../xml-tools/sample-xsd-file-purchase-order-schema.md) , puis collez-le pour remplacer le code qui a été ajouté par défaut au nouveau fichier XSD.

4. Sélectionnez l’élément `purchaseOrder` dans l’Explorateur de schémas en cliquant avec le bouton droit sur l’élément `purchaseOrder` dans l’éditeur XML, puis en sélectionnant **afficher dans l’Explorateur XML**.

5. Cliquez avec le bouton droit sur le `purchaseOrder` dans l’Explorateur XML et sélectionnez **afficher en vue de modèle de contenu**.

     La vue de modèle de contenu affiche l'élément `purchaseOrder` sur son aire de conception.

6. Développez les nœuds`shipTo`, `billTo` et `items` en double-cliquant sur chaque nœud ou en cliquant sur la flèche double à droite de chaque nœud.

     Les nœuds de l'élément `purchaseOrder` sont maintenant développés et vous pouvez consulter le modèle de contenu de l'élément.

7. Cliquez sur n'importe quel nœud sous l'élément `purchaseOrder`, puis examinez la barre de fil d'Ariane (breadcrumb) pour déterminer l'emplacement du nœud sélectionné dans le jeu de schémas.

8. Cliquez sur le bouton **afficher la documentation** dans la barre d’outils XSD pour basculer documentation. Vous pouvez également cliquer avec le bouton droit sur l'aire de conception pour basculer vers la documentation.

9. Rick-cliquez sur le nœud `purchaseOrder`, puis sélectionnez **générer un exemple de code XML** pour afficher le document de l’instance XML.

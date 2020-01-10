---
title: Examiner des nœuds à l’aide de la vue de modèle de contenu dans le concepteur de schémas XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5a7e6e311a4fbd02973edf94c6eb117f69d6cea
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592709"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Comment : examiner le modèle de contenu des nœuds à l’aide de la vue de modèle de contenu

Cette rubrique explique comment explorer vos nœuds à l’aide de la [vue de modèle de contenu](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Pour créer un fichier XSD et afficher l'élément racine dans la vue de modèle de contenu

1. Créez un fichier de schéma XML.

2. Cliquez sur **utiliser l’éditeur XML pour afficher et modifier le fichier de schéma XML sous-jacent** dans la vue de départ.

3. Copiez l’exemple de code XML à partir de exemple de schéma [XML : schéma de bon de commande](../xml-tools/sample-xsd-file-purchase-order-schema.md) , puis collez-le pour remplacer le code qui a été ajouté par défaut au nouveau fichier XSD.

4. Sélectionnez l’élément `purchaseOrder` dans l’Explorateur de schémas en cliquant avec le bouton droit sur l’élément `purchaseOrder` dans l’éditeur XML, puis en sélectionnant **afficher dans l’Explorateur XML**.

5. Cliquez avec le bouton droit sur le `purchaseOrder` dans l’Explorateur XML et sélectionnez **afficher en vue de modèle de contenu**.

     La vue de modèle de contenu affiche l'élément `purchaseOrder` sur son aire de conception.

6. Développez les nœuds`shipTo`, `billTo` et `items` en double-cliquant sur chaque nœud ou en cliquant sur la flèche double à droite de chaque nœud.

     Les nœuds de l'élément `purchaseOrder` sont maintenant développés et vous pouvez consulter le modèle de contenu de l'élément.

7. Cliquez sur n'importe quel nœud sous l'élément `purchaseOrder`, puis examinez la barre de fil d'Ariane (breadcrumb) pour déterminer l'emplacement du nœud sélectionné dans le jeu de schémas.

8. Cliquez sur le bouton **afficher la documentation** dans la barre d’outils XSD pour activer ou désactiver la documentation. Vous pouvez également cliquer avec le bouton droit sur l'aire de conception pour basculer vers la documentation.

9. Cliquez avec le bouton droit sur le nœud `purchaseOrder`, puis sélectionnez **générer un exemple de code XML** pour afficher le document de l’instance XML.

---
title: 'Procédure : Basculer entre les vues et l’éditeur XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09ad752dc87ea322396d6e6513593d71a7554b98
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936241"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Procédure : Basculer entre les vues et l’éditeur XML

Cette rubrique montre comment basculer entre les vues XML du Concepteur de schémas XML (Concepteur XSD) et l'Éditeur XML. Cet exemple utilise le [schéma de bon de commande](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Pour basculer entre les vues et l'Éditeur XML

1.  Pour créer et modifier un fichier de schéma XML, suivez les étapes de [Comment : Créer et modifier un fichier de schéma XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Pour basculer vers le Concepteur de schémas XML à partir de l’éditeur XML, cliquez sur n’importe où dans l’éditeur XML et sélectionnez **Concepteur de vues**.

3.  Pour basculer vers la vue du graphique à l’aide de la limite, cliquez sur le **utiliser la vue du graphique pour voir la relation entre les nœuds** lien sur la vue de départ.

4.  Faites glisser le `USAddress` nœud à partir de la **Explorateur de schémas XML** sur la vue du graphique. Cliquez sur le `USAddress` nœud dans la vue du graphique, puis sélectionnez **afficher en vue de modèle de contenu** dans le menu contextuel.

     La vue de modèle de contenu avec les détails du nœud `USAddress` s'affiche.

5.  Pour basculer vers la vue de départ à partir de la vue de modèle de contenu à l’aide de la barre d’outils, cliquez sur le **vue de départ** dans la barre d’outils XSD.

6.  Pour basculer entre les vues à l’aide des raccourcis clavier, appuyez sur **Ctrl**+**1** pour la vue de départ, **Ctrl**+**2** pour la vue du graphique, et **Ctrl**+**3** pour la vue de modèle de contenu.

7.  Pour accéder à l’éditeur XML à partir de l’affichage du modèle de contenu, cliquez sur le nœud et sélectionnez **afficher le Code** dans le menu contextuel.
---
title: 'Procédure : basculer entre les vues et l’éditeur XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28267f705dd9a747d0e3f3ac5dc2869ab7de8f6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656317"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Procédure : basculer entre les vues et l'Éditeur XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique montre comment basculer entre les vues XML du Concepteur de schémas XML (Concepteur XSD) et l'Éditeur XML. Cet exemple utilise le [schéma de bon de commande](../xml-tools/sample-xsd-file-simple-schema.md).

### <a name="to-switch-between-the-views-and-the-xml-editor"></a>Pour basculer entre les vues et l'Éditeur XML

1. Pour créer et modifier un nouveau fichier de schéma XML, suivez les étapes de la rubrique [Comment : créer et modifier un fichier de schéma XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Pour basculer vers le concepteur de schémas XML à partir de l’éditeur XML, cliquez avec le bouton droit n’importe où dans l’éditeur XML et sélectionnez **Concepteur de vues**.

3. Pour basculer vers la vue du graphique à l’aide du filigrane, cliquez sur le lien **utiliser la vue du graphique pour afficher la relation entre les nœuds** dans la vue de départ.

4. Faites glisser le nœud `USAddress` de l'Explorateur de schémas XML sur la vue du graphique. Cliquez avec le bouton droit sur le `USAddress` nœud dans la vue du graphique, puis sélectionnez **afficher en vue de modèle de contenu** dans le menu contextuel.

     La vue de modèle de contenu avec les détails du nœud `USAddress` s'affiche.

5. Pour basculer vers la vue de départ à partir de la vue de modèle de contenu à l'aide de la barre d'outils, cliquez sur le bouton Vue de départ dans la barre d'outils XSD.

6. Pour basculer entre les vues à l'aide des touches rapides, appuyez sur Ctrl+1 pour la vue de départ, sur Ctrl+2 pour la vue du graphique, et sur Ctrl+3 pour la vue de modèle de contenu.

7. Pour accéder à l’éditeur XML à partir de la vue de modèle de contenu, cliquez avec le bouton droit sur le nœud et sélectionnez **afficher le code** dans le menu contextuel.

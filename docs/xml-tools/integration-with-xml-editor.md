---
title: Intégration du Concepteur de schémas XML avec l’éditeur XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e2cb44f3416aabfa859d4a8ef2126003b3ce59e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992124"
---
# <a name="integration-with-xml-editor"></a>Intégration avec l’éditeur XML

Le Concepteur de schémas XML est intégré à l'Éditeur XML. Si vous modifiez un fichier XSD dans l’éditeur XML, la modification apparaîtront dans le [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md). Si vous avez le [vue du graphique](../xml-tools/graph-view.md) ou [affichage du modèle de contenu](../xml-tools/content-model-view.md) ouvert, la modification est également répercutée il. Vous pouvez naviguer entre le Concepteur de schémas XML et l'Éditeur XML des façons suivantes :

-   Dans l’éditeur XML, cliquez sur un nœud et sélectionnez **afficher dans l’Explorateur de schémas XML**.

-   Dans la vue du graphique et le **Explorateur de schémas XML**, double-cliquez sur un nœud, ou cliquez sur un nœud et sélectionnez **afficher le Code**. Dans la vue de modèle de contenu, cliquez sur un nœud et sélectionnez **afficher le Code**.

La capture d’écran suivante montre un schéma XML ouvert dans le **Explorateur de schémas XML**. Le **Explorateur de schémas XML** affiche le schéma défini dans une arborescence. L’éditeur XML affiche la vue de texte du nœud qui est actuellement actif dans le **Explorateur de schémas XML**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Il est parfois utile d'examiner le code avec l'Éditeur XML et le concepteur graphique côte à côte. Pour afficher les deux fichiers en même temps, cliquez n’importe où dans l’éditeur XML, puis sélectionnez **Concepteur de vues**. Dans le menu Visual Studio Windows, sélectionnez **nouveau Horizontal (ou Vertical) groupe d’onglets**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Voir aussi

- [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md)
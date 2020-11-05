---
title: Intégration du concepteur de schémas XML avec l’éditeur XML
description: En savoir plus sur l’intégration entre le concepteur de schémas XML et l’éditeur XML, et la façon dont les modifications apportées dans l’une sont reflétées dans l’autre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9569e33f8f9f861bc5d89030c6fe38b0ab853a6f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400185"
---
# <a name="integration-with-xml-editor"></a>Intégration avec l’éditeur XML

Le concepteur de schémas XML est intégré à l’éditeur XML. Si vous modifiez un fichier XSD dans l’éditeur XML, la modification sera reflétée dans l' [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md). Si la vue du [graphique](../xml-tools/graph-view.md) ou la [vue de modèle de contenu](../xml-tools/content-model-view.md) est ouverte, la modification y sera également reflétée. Vous pouvez naviguer entre le concepteur de schémas XML et l’éditeur XML de l’une des manières suivantes :

- Dans l’éditeur XML, cliquez avec le bouton droit sur un nœud et sélectionnez **afficher dans l’Explorateur de schémas XML**.

- Dans la vue du graphique et l' **Explorateur de schémas XML** , double-cliquez sur un nœud, ou cliquez avec le bouton droit sur un nœud et sélectionnez **afficher le code**. Dans la vue de modèle de contenu, cliquez avec le bouton droit sur un nœud et sélectionnez **afficher le code**.

La capture d’écran suivante montre un schéma XML ouvert dans l' **Explorateur de schémas XML**. L' **Explorateur de schémas XML** affiche le jeu de schémas dans une arborescence. L’éditeur XML affiche la vue de texte du nœud qui est actuellement actif dans l' **Explorateur de schémas XML**.

![Capture d’écran d’un projet Visual Studio montrant un nœud XML dans le volet de l’éditeur XML et une arborescence du jeu de schémas dans le volet Explorateur de schémas XML.](../xml-tools/media/xsddesignerwithxmleditor.gif)

Il est parfois utile de voir le code dans l’éditeur XML et le concepteur graphique côte à côte. Pour afficher les deux fichiers en même temps, cliquez avec le bouton droit n’importe où dans l’éditeur XML et sélectionnez **Concepteur de vues**. Dans le menu Windows de Visual Studio, sélectionnez **nouveau groupe d’onglets horizontal (ou vertical)**.

![Capture d’écran d’un projet Visual Studio montrant le volet Concepteur de vues, le volet éditeur XML et le volet Explorateur de schémas XML.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Voir aussi

- [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md)

---
title: Fenêtres de document | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d29d64090320a8f62491209773145c024564efa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186630"
---
# <a name="document-windows"></a>Fenêtres de document
Dans Visual Studio, une *fenêtre de document* est une fenêtre enfant encadrée qui est associée à une fenêtre d’interface multidocument (MDI, multiple-document interface). Les fenêtres de document sont généralement utilisées pour l’affichage et la modification du code source ou du texte, mais elles peuvent également héberger d’autres types fonctionnels. Fenêtres de document :

- Peut être organisé dans des groupes d’onglets horizontaux ou verticaux séparés dans le MDI parent afin que plusieurs fichiers puissent être affichés en même temps.

- Peuvent être ancrées dans n’importe quel ordre dans l’MDI parent.

- Peut être flottant librement.

- Sont liés dans l’ordre de tabulation aux autres fenêtres MDI.

  Les commandes de regroupement, d’ancrage et de flottement sont accessibles dans le menu contextuel d’un onglet de fenêtre de document.

  Pour plus d’informations sur le comportement des fenêtres dans Visual Studio, consultez [personnaliser les dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implémentation de la fenêtre de document
 Les fenêtres de document sont créées en implémentant un éditeur. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> crée des fenêtres de document dans le cadre de l’instanciation d’un éditeur. Pour plus d’informations, consultez [interfaces héritées dans l’éditeur](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Pour fournir des points de navigation arrière et avant dans une fenêtre, implémentez l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation>. L’éditeur de texte utilise des marqueurs de texte pour identifier les points de navigation dans le document.

## <a name="the-running-document-table"></a>Table de document en cours d’exécution
 L’IDE utilise la table de document en cours d’exécution (RDT) pour suivre l’état de chaque fenêtre de document. Le RDT est le mécanisme par lequel les fenêtres de document sont notifiées des événements, par exemple lorsqu’une solution est fermée ou lorsqu’un fichier a été modifié. Pour plus d’informations, consultez exécution de la [table des documents](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Voir aussi
- [Chargement différé du document](../../extensibility/internals/delayed-document-loading.md)
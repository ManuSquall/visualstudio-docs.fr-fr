---
title: Fenêtres de document | Microsoft Docs
description: Découvrez les fenêtres de document dans Visual Studio, notamment comment les implémenter et comment la table de document en cours d’exécution (RDT) effectue le suivi de leur état.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: df7a797c0b4587698197412f49eef6bfab183a7a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899912"
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
 Les fenêtres de document sont créées en implémentant un éditeur. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface crée des fenêtres de document dans le cadre de l’instanciation d’un éditeur. Pour plus d’informations, consultez [interfaces héritées dans l’éditeur](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Pour fournir des points de navigation arrière et avant dans une fenêtre, implémentez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interface. L’éditeur de texte utilise des marqueurs de texte pour identifier les points de navigation dans le document.

## <a name="the-running-document-table"></a>Table de document en cours d’exécution
 L’IDE utilise la table de document en cours d’exécution (RDT) pour suivre l’état de chaque fenêtre de document. Le RDT est le mécanisme par lequel les fenêtres de document sont notifiées des événements, par exemple lorsqu’une solution est fermée ou lorsqu’un fichier a été modifié. Pour plus d’informations, consultez exécution de la [table des documents](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Voir aussi
- [Chargement différé du document](../../extensibility/internals/delayed-document-loading.md)

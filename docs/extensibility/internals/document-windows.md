---
title: Document Windows (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708514"
---
# <a name="document-windows"></a>Fenêtres de document
Dans Visual Studio, une *fenêtre de document* est une fenêtre d’enfant encadrée qui est associée à une fenêtre d’interface multi-documents (MDI). Les fenêtres de documents sont généralement utilisées pour l’affichage et la modification du code source ou du texte, mais elles peuvent également héberger d’autres types fonctionnels. Fenêtres de document:

- Peut être organisé en groupes d’onglets horizontaux ou verticaux distincts dans le MDI parent de sorte que plusieurs fichiers peuvent être consultés en même temps.

- Peut être amarré dans n’importe quel ordre dans le MDI parent.

- Peut être flotté librement.

- Sont reliés dans l’onglet afin d’autres fenêtres MDI.

  Les commandes de regroupement, d’amarrage et de flottement peuvent être trouvées sur le menu raccourci pour un onglet de fenêtre de document.

  Pour plus d’informations sur le comportement des fenêtres dans Visual Studio, voir [personnaliser les mises en page des fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Mise en œuvre de fenêtre documentaire
 Les fenêtres de documents sont créées par la mise en œuvre d’un éditeur. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> crée des fenêtres de documents dans le cadre de l’instantanément d’un éditeur. Pour plus d’informations, voir [les interfaces Legacy dans l’éditeur](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Pour fournir des points de navigation vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> l’arrière et vers l’avant dans une fenêtre, implémentez l’interface. L’éditeur de texte utilise des marqueurs texte pour identifier les points de navigation dans le document.

## <a name="the-running-document-table"></a>La table de document De fonctionnement
 L’IDE utilise le tableau de documents Running (RDT) pour suivre l’état de chaque fenêtre de document. Le RDT est le mécanisme par lequel les fenêtres de documents sont notifiées des événements, comme lorsqu’une solution est fermée ou lorsqu’un fichier a été modifié. Pour plus d’informations, voir [tableau de document Running](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Voir aussi
- [Chargement de documents retardé](../../extensibility/internals/delayed-document-loading.md)

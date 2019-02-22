---
title: Document Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d53cb3298ec3a8190f79ad87bd89e646ccbafbe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633211"
---
# <a name="document-windows"></a>Fenêtres de document
Dans Visual Studio, un *fenêtre de document* est une fenêtre enfant encadré qui est associée à une fenêtre d’interface multidocument (MDI). Fenêtres de document sont généralement utilisés pour l’affichage et la modification de code source ou de texte, mais elles peuvent héberger également d’autres types fonctionnels. Fenêtres de document :

- Peuvent être organisés dans des groupes distincts onglet horizontal ou vertical dans le parent MDI afin que plusieurs fichiers peuvent être affichées en même temps.

- Peuvent être ancrées dans n’importe quel ordre dans le parent MDI.

- Peut flotter librement.

- Sont liées dans l’ordre de tabulation à d’autres fenêtres MDI.

  Les commandes pour le regroupement, ancrer et rendre flottantes sont accessibles dans le menu contextuel d’un onglet de fenêtre de document.

  Pour plus d’informations sur le comportement de la fenêtre dans Visual Studio, consultez [personnaliser les dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implémentation de fenêtres de document
 Les fenêtres de document sont créées en implémentant un éditeur. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface crée des fenêtres de document dans le cadre de l’instanciation d’un éditeur. Pour plus d’informations, consultez [hérité interfaces dans l’éditeur](../../extensibility/legacy-interfaces-in-the-editor.md).

> [!NOTE]
>  Pour fournir en arrière et transférer des points de navigation dans une fenêtre, vous devez implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interface. L’éditeur de texte utilise des marqueurs de texte pour identifier les points de navigation dans le document.

## <a name="the-running-document-table"></a>La table de document en cours d’exécution
 L’IDE utilise la table de document en cours d’exécution (RDT) pour suivre l’état de chaque fenêtre de document. La RDT est le mécanisme via quel document windows sont informés des événements, tels que lors de la fermeture d’une solution ou un fichier a été modifié. Pour plus d’informations, consultez [table de documents en cours d’exécution](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Voir aussi
- [Chargement de document différé](../../extensibility/internals/delayed-document-loading.md)
---
title: Implémentation de la gestion des commandes pour les projets imbriqués | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 628fde153441104e4bb504253d96235270b4b8fb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727081"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implémentation de la gestion des commandes pour les projets imbriqués
L’IDE peut passer des commandes qui sont transmises via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> et les interfaces <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> à des projets imbriqués, ou les projets parents peuvent filtrer ou substituer les commandes.

> [!NOTE]
> Seules les commandes gérées normalement par le projet parent peuvent être filtrées. Les commandes telles que **générer** et **déployer** qui sont gérées par l’IDE ne peuvent pas être filtrées.

 Les étapes suivantes décrivent le processus d’implémentation de la gestion des commandes.

## <a name="procedures"></a>Procédures

#### <a name="to-implement-command-handling"></a>Pour implémenter la gestion des commandes

1. Lorsque l’utilisateur sélectionne un projet imbriqué ou un nœud dans un projet imbriqué :

   1. L’IDE appelle la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>.

      — ou —

   2. Si la commande provient d’une fenêtre de hiérarchie, telle qu’une commande de menu contextuel dans Explorateur de solutions, l’IDE appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> sur le parent du projet.

2. Le projet parent peut examiner les paramètres à passer à `QueryStatus`, tels que `pguidCmdGroup` et `prgCmds`, pour déterminer si le projet parent doit filtrer les commandes. Si le projet parent est implémenté pour filtrer les commandes, il doit définir :

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Le projet parent doit alors retourner `S_OK`.

    Si le projet parent ne filtre pas la commande, il doit simplement retourner `S_OK`. Dans ce cas, l’IDE achemine automatiquement la commande vers le projet enfant.

    Le projet parent n’a pas besoin d’acheminer la commande vers le projet enfant. L’IDE effectue cette tâche..

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)
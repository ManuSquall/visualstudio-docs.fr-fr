---
title: Mise en œuvre de la gestion des commandes pour les projets imbriqués (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707606"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implémentation de la gestion des commandes pour les projets imbriqués
L’IDE peut passer des commandes <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> qui <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> passent à travers les et les interfaces de projets imbriqués, ou les projets parentaux peuvent filtrer ou remplacer les commandes.

> [!NOTE]
> Seules les commandes habituellement gérées par le projet parent peuvent être filtrées. Les commandes telles que **Construire** et **déployer** qui sont traitées par l’IDE ne peuvent pas être filtrées.

 Les étapes suivantes décrivent le processus de mise en œuvre du traitement des commandes.

## <a name="procedures"></a>Procédures

#### <a name="to-implement-command-handling"></a>Mettre en œuvre la manutention des commandes

1. Lorsque l’utilisateur choisit un projet imbriqué ou un nœud dans un projet imbriqué :

   1. L’IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> appelle la méthode.

      — ou —

   2. Si la commande provient d’une fenêtre de hiérarchie, comme une commande <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> de menu raccourci dans Solution Explorer, l’IDE appelle la méthode sur le parent du projet.

2. Le projet parent peut examiner les `QueryStatus`paramètres `pguidCmdGroup` à `prgCmds`transmettre, tels que, pour déterminer si le projet parent doit filtrer les commandes. Si le projet parent est mis en œuvre pour filtrer les commandes, il doit définir :

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Ensuite, le projet `S_OK`parent devrait revenir .

    Si le projet parent ne filtre pas `S_OK`la commande, il devrait simplement revenir . Dans ce cas, l’IDE achemine automatiquement la commande vers le projet enfant.

    Le projet parent n’a pas à acheminer la commande vers le projet enfant. L’IDE effectue cette tâche.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)

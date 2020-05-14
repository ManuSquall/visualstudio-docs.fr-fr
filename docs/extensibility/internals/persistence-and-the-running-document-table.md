---
title: Persistance et la table de documents de fonctionnement ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706716"
---
# <a name="persistence-and-the-running-document-table"></a>Persistance et table de document en cours d’exécution
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’IDE, les projets sont entièrement responsables de la gestion <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>de la persistance de leurs éléments de projet, qu’ils accomplissent en utilisant le service, . Les documents sont l’unité de base de la persistance dans l’environnement Visual Studio. Les projets coordonnent l’ouverture, l’enregistrement et le changement de nom des documents avec la table de documents en cours d’exécution (RDT), une ressource qui suit l’état de tous les documents ouverts.

## <a name="managing-persistence"></a>Gérer la persistance
 Les projets contrôlent le service <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> de persistance de l’environnement en mettant en œuvre l’interface. Bien que l’environnement ne demande jamais directement à un document de se poursuivre, il demande au projet (ou hiérarchie) de sauver le document. Cela permet au projet d’enregistrer ses données d’élément de projet dans des fichiers locaux, des fichiers distants, une base de données, un référentiel ou un autre support.

 L’environnement mondial maintient le RDT. L’environnement conserve les entrées pour toutes les fenêtres ouvertes et les documents dans le RDT, ce qui leur permet de recevoir des notifications spéciales, par exemple lorsqu’une solution est fermée. En outre, le RDT permet à l’environnement de suivre leurs nœuds correspondants dans **Solution Explorer**. Le RDT conserve un enregistrement par objet ouvert et persistant, y compris les dossiers de projet et les documents d’élément de projet.

## <a name="see-also"></a>Voir aussi
- [Exécution de la table de document](../../extensibility/internals/running-document-table.md)
- [Sélection et devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

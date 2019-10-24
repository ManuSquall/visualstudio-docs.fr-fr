---
title: Persistance et la table de documents en cours d’exécution | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f03836e1faaac03fbd89c0b93f37a698cbdcd56a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726079"
---
# <a name="persistence-and-the-running-document-table"></a>Persistance et table de document en cours d’exécution
Dans l’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], les projets sont entièrement responsables de la gestion de la persistance de leurs éléments de projet, qu’ils effectuent à l’aide du service, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Les documents sont l’unité de persistance de base dans l’environnement Visual Studio. Les projets coordonnent l’ouverture, l’enregistrement et le changement de nom des documents avec la table de documents en cours d’exécution (RDT), une ressource qui suit l’état de tous les documents ouverts.

## <a name="managing-persistence"></a>Gestion de la persistance
 Les projets contrôlent le service de persistance de l’environnement en implémentant l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>. Alors que l’environnement ne demande jamais directement à un document de persister, il demande au projet propriétaire (ou à la hiérarchie) d’enregistrer le document. Cela permet au projet d’enregistrer ses données d’élément de projet dans des fichiers locaux, des fichiers distants, une base de données, un référentiel ou un autre support.

 L’environnement global gère le RDT. L’environnement contient des entrées pour toutes les fenêtres et tous les documents ouverts dans RDT, ce qui leur permet de recevoir des notifications spéciales, par exemple quand une solution est fermée. En outre, l’RDT permet à l’environnement de suivre les nœuds correspondants dans **Explorateur de solutions**. Le RDT gère un enregistrement par objet persistant ouvert, y compris les fichiers projet et les documents d’élément de projet.

## <a name="see-also"></a>Voir aussi
- [Exécution de la table de document](../../extensibility/internals/running-document-table.md)
- [Sélection et devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
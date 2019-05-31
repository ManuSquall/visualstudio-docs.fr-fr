---
title: Persistance et l’exécution de Table de documents | Microsoft Docs
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
ms.openlocfilehash: d80932ab926b7ef26eaef10991e4f5782e81c4b5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328520"
---
# <a name="persistence-and-the-running-document-table"></a>Persistance et table de document en cours d’exécution
Dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, les projets sont entièrement responsables de la gestion de leurs éléments de projet, ils accomplir à l’aide du service, la persistance <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Les documents sont l’unité élémentaire de persistance dans l’environnement Visual Studio. Projets coordonnent l’ouverture, l’enregistrement et changement de nom des documents avec la table document en cours d’exécution (RDT), une ressource qui effectue le suivi de l’état de tous les documents ouverts.

## <a name="managing-persistence"></a>Gestion de la persistance
 Projets de contrôle de service de persistance de l’environnement en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interface. Alors que l’environnement de demande jamais directement à un document à persévérer, il demande le projet propriétaire (ou hiérarchie) pour enregistrer le document. Cela rend possible pour le projet enregistrer ses données d’élément de projet dans les fichiers locaux, les fichiers à distance, une base de données, un référentiel ou un autre support.

 L’environnement global conserve la RDT. L’environnement comprend des entrées pour toutes les fenêtres ouvertes et documents dans le RDT, ce qui rend possible pour qu’ils puissent recevoir des notifications spéciales, telles que lors de la fermeture d’une solution. En outre, la RDT rend possible pour l’environnement effectuer le suivi de leurs nœuds correspondants dans **l’Explorateur de solutions**. La RDT conserve un enregistrement par objet ouvert, persistant, y compris les fichiers projet et les documents de l’élément de projet.

## <a name="see-also"></a>Voir aussi
- [Exécution de la table de document](../../extensibility/internals/running-document-table.md)
- [Sélection et devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
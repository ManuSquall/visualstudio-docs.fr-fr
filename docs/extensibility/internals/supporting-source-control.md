---
title: Contrôle de code source pris en charge | Microsoft Docs
description: Découvrez comment Visual Studio prend en charge les extractions de fichiers, les archivages et d’autres opérations de contrôle de code source pour votre projet ou votre éditeur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6923eb7a534a4cacf8062883d073ddddc9395e17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892552"
---
# <a name="supporting-source-control"></a>Prise en charge du contrôle de code source
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge les extractions de fichiers, les archivages et d’autres opérations de contrôle de code source pour votre projet ou votre éditeur. En tant que client de contrôle de code source, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est conçu pour interagir avec un package de contrôle de code source, tel que [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] , qui fournit des fonctionnalités d’archivage, de contrôle de version et de contrôle pour un ensemble de fichiers défini dynamiquement.

## <a name="in-this-section"></a>Dans cette section
- [Modèle des packages de contrôle de code source](../../extensibility/internals/model-for-source-control-packages.md)

 Décrit les interfaces qu’un type de projet doit implémenter pour prendre en charge le contrôle de code source.

- [Décisions de conception](../../extensibility/internals/source-control-design-decisions.md)

 Fournit des questions dont les réponses modifient la façon dont vous implémentez un type de projet.

- [Détails de configuration](../../extensibility/internals/source-control-configuration-details.md)

 Décrit comment la prise en charge du contrôle de code source modifie l’implémentation d’un type de projet.

- [Instructions supplémentaires pour les projets et les éditeurs](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Décrit les meilleures pratiques pour les types de projet et les éditeurs.

- [Détails du runtime](../../extensibility/internals/source-control-runtime-details.md)

 Décrit comment inscrire un projet lorsqu’un utilisateur l’ajoute à un système de contrôle de code source.

## <a name="reference"></a>Référence
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Indique à l’environnement ou au package de contrôle de code source qu’un fichier va être modifié en mémoire ou enregistré.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> Permet aux projets et aux hiérarchies de s’inscrire auprès du contrôle de code source et d’obtenir des informations sur l’état du contrôle de code source.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Implémenté dans un système de projet pour fournir le contrôle de code source pour les fichiers projet et les éléments de projet.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Utilisé par les projets pour demander à l’environnement l’autorisation d’ajouter, de supprimer ou de renommer un fichier ou un répertoire dans une solution.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> Avertit les clients des modifications apportées aux fichiers ou répertoires du projet.

## <a name="related-sections"></a>Sections connexes
- [Types de projets](../../extensibility/internals/project-types.md)

 Fournit une vue d’ensemble des projets en tant que blocs de construction de base de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE). Des liens sont fournis vers des rubriques supplémentaires qui expliquent comment les projets contrôlent la génération et la compilation du code.

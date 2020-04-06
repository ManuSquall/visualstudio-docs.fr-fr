---
title: Soutien au contrôle des sources (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704727"
---
# <a name="supporting-source-control"></a>Prise en charge du contrôle de code source
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]prend en charge les caisses de fichiers, les check-ins et d’autres opérations de contrôle des sources pour votre projet ou votre éditeur. En tant que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] client de contrôle source, est conçu [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]pour interagir avec un paquet de contrôle source, tels que , qui fournit des installations d’archivage, de version et de contrôle pour un ensemble dynamiquement défini de fichiers.

## <a name="in-this-section"></a>Dans cette section
- [Modèle des packages de contrôle de code source](../../extensibility/internals/model-for-source-control-packages.md)

 Décrit les interfaces qu’un type de projet doit mettre en œuvre pour prendre en charge le contrôle des sources.

- [Décisions de conception](../../extensibility/internals/source-control-design-decisions.md)

 Fournit des questions dont les réponses changent la façon dont vous implémentez un type de projet.

- [Détails de configuration](../../extensibility/internals/source-control-configuration-details.md)

 Décrit comment le contrôle à la source de soutien modifie la mise en œuvre d’un type de projet.

- [Instructions supplémentaires pour les projets et les éditeurs](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Discute des meilleures pratiques pour les types de projets et les éditeurs.

- [Détails du runtime](../../extensibility/internals/source-control-runtime-details.md)

 Décrit comment enregistrer un projet lorsqu’un utilisateur l’ajoute à un système de contrôle des sources.

## <a name="reference"></a>Informations de référence
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>Indique à l’environnement ou au paquet de contrôle source qu’un fichier est sur le point d’être changé dans la mémoire ou enregistré.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>Permet aux projets et aux hiérarchies de s’enregistrer avec le contrôle des sources et d’obtenir des informations sur l’état du contrôle des sources.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>Mise en œuvre dans un système de projet pour assurer le contrôle des sources pour les dossiers de projets et les éléments du projet.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>Utilisé par les projets pour interroger l’environnement pour obtenir l’autorisation d’ajouter, de supprimer ou de renommer un fichier ou un répertoire dans une solution.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>Informe les clients des changements apportés aux dossiers de projet ou aux répertoires.

## <a name="related-sections"></a>Sections connexes
- [Types de projets](../../extensibility/internals/project-types.md)

 Fournit un aperçu des projets comme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éléments de base de l’environnement de développement intégré (IDE). Des liens sont fournis à d’autres sujets qui expliquent comment les projets contrôlent la construction et la compilation du code.

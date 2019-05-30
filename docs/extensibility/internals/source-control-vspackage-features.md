---
title: Fonctionnalités de VSPackage de contrôle de source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 513f43787040075ea0904c97b1aca9866359520a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322490"
---
# <a name="source-control-vspackage-features"></a>Fonctionnalités de VSPackage de contrôle de code source
Cette section décrit les différentes fonctionnalités d’un VSPackage de contrôle de code source. Il décrit l’inscription et sélection de détails pour un package Visual Studio et traite des trois fonctionnalités liées au contrôle source principal : gestion des événements enregistrer de la requête de modification de la requête (QEQS), de remplacement de glyphe et interface utilisateur personnalisée (interface utilisateur) pour le contrôle de code source fonctions.

## <a name="in-this-section"></a>Dans cette section
- [Inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Décrit les mécanismes de l’inscription et la sélection du package.

- [QEQS (Query Edit Query Save)](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Explique le rôle de requête de modification de la requête-enregistrer les événements et comment elles sont gérées par le VSPackage de contrôle de code source.

- [Contrôle de glyphe](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Décrit les niveaux de contrôle de glyphe et comment les implémenter.

- [Interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Décrit les éléments d’interface utilisateur un VSPackage de contrôle de code source peut spécifier.

## <a name="related-sections"></a>Rubriques connexes
- [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Explique comment créer un contrôle de code source VSPackage qui non seulement fournit des fonctionnalités de contrôle de code source, mais peut être utilisé pour personnaliser le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur de contrôle de code source.
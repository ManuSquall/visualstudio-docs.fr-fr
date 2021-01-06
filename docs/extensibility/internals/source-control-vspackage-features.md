---
title: Fonctionnalités du VSPackage de contrôle de code source | Microsoft Docs
description: Découvrez les fonctionnalités d’un VSPackage de contrôle de code source, notamment les détails d’inscription et de sélection, ainsi que certaines des principales fonctionnalités liées au contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dd887488adc5813ad51c9fa2a25648e25ab4876
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876218"
---
# <a name="source-control-vspackage-features"></a>Fonctionnalités de VSPackage de contrôle de code source
Cette section décrit les différentes fonctionnalités d’un VSPackage de contrôle de code source. Il présente les détails de l’inscription et de la sélection pour un tel VSPackage, et présente trois des principales fonctionnalités liées au contrôle de code source : la gestion des événements de Query-Edit Query-Save (provenant QEQS), le remplacement de glyphes et l’interface utilisateur personnalisée pour les fonctions de contrôle de code source.

## <a name="in-this-section"></a>Dans cette section
- [Inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Décrit les mécanismes d’inscription et de sélection des packages.

- [QEQS (Query Edit Query Save)](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Explique le rôle de Query-Edit événements Query-Save et la façon dont ils sont gérés par le VSPackage de contrôle de code source.

- [Contrôle de glyphe](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Décrit les niveaux de contrôle de glyphe et comment les implémenter.

- [Interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Décrit les éléments d’interface utilisateur qu’un VSPackage de contrôle de code source peut spécifier.

## <a name="related-sections"></a>Sections connexes
- [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Explique comment créer un VSPackage de contrôle de code source qui fournit non seulement une fonctionnalité de contrôle de code source, mais qui peut être utilisé pour personnaliser l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface utilisateur du contrôle de code source.

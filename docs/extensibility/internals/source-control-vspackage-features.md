---
title: Fonctionnalités du VSPackage de contrôle de code source | Microsoft Docs
description: Découvrez les fonctionnalités d’un VSPackage de contrôle de code source, notamment les détails d’inscription et de sélection, ainsi que certaines des principales fonctionnalités liées au contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd501aa6d1fc3189d5008d76deb56dd570d03d8e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064122"
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

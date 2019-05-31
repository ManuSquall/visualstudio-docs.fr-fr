---
title: Éléments de conception de VSPackage de contrôle source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e9b22ea32698d6e996bfee618b0b5ca4da5943d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322478"
---
# <a name="source-control-vspackage-design-elements"></a>Éléments de conception de VSPackage de contrôle de source
Les rubriques de cette section décrivent la structure le VSPackage doit implémenter pour l’intégration approfondie de contrôle de code source. Il répertorie également les interfaces et les services que la source de contrôle VSPackage peuvent implémenter, et utiliser les interfaces et les services le VSPackage de contrôle de code source à partir d’autres [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composants pour prendre en charge de sa source de contrôlent le modèle et les fonctionnalités.

## <a name="in-this-section"></a>Dans cette section
- [Structure VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Définit la structure de contrôle de source de package Visual Studio.

- [Interfaces et services associés](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Répertorie les interfaces d’associées au package de contrôle de source et de services.

- [Services fournis](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Décrit le service de contrôle de code source fourni par le VSPackage de contrôle de code source.

## <a name="related-sections"></a>Rubriques connexes
- [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Explique comment créer un contrôle de code source VSPackage qui non seulement fournit des fonctionnalités de contrôle de code source, mais peut être utilisé pour personnaliser le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur de contrôle de code source.
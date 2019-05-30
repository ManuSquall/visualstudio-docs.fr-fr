---
title: Déploiement des Types de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac03682fa1158f5da9c694cf1be5282717c07b55
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312178"
---
# <a name="deploy-project-types"></a>Déployer des types de projets
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] installe une nouvelle agrégation de type de projet (*ProjectAggregator2.dll*) et également un package de programme d’installation de Windows pour la redistribution (*ProjectAggregator2.msi*). Vous devez utiliser le nouvel aggregator pour les types de projets de code managé. ProjectAggregator2 articulé autour des limitations dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet aggregator qui empêche des types de projets de code managé de fonctionner correctement. Les étapes suivantes décrivent comment modifier votre VSPackage pour utiliser le nouvel aggregator.

1. Supprimer le projet NativeHierarchyWrapper de votre solution.

2. Supprimer les fichiers binaires NativeHierarchyWrapper à partir de votre installation.

3. Ajouter *ProjectAggregator2.msi* à votre installation.
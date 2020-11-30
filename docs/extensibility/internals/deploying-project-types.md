---
title: Déploiement des types de projets | Microsoft Docs
description: Découvrez comment déployer des types de projets de code managé à l’aide d’une nouvelle agrégation de type projet et Windows Installer Package pour la redistribution, dans le kit de développement logiciel (SDK) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1b015f29b6521482013a77bbcf7c44d8a79afa6
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329872"
---
# <a name="deploy-project-types"></a>Déployer des types de projet
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] installe une nouvelle agrégation de type projet (*ProjectAggregator2.dll*) et également un package Windows Installer pour la redistribution (*ProjectAggregator2.msi*). Vous devez utiliser le nouvel agrégateur pour les types de projets de code managé. ProjectAggregator2 contourne les limites de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] agrégateur de projet qui empêche les types de projets de code managé de fonctionner correctement. Les étapes suivantes décrivent comment modifier votre VSPackage pour utiliser le nouvel agrégateur.

1. Supprimez le projet NativeHierarchyWrapper de votre solution.

2. Supprimez tous les fichiers binaires NativeHierarchyWrapper de votre installation.

3. Ajoutez *ProjectAggregator2.msi* à votre installation.

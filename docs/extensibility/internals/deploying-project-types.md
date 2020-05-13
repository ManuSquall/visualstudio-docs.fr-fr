---
title: Déploiement des types de projets (en anglais seulement) Microsoft Docs
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
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708790"
---
# <a name="deploy-project-types"></a>Déployer les types de projets
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]installe un nouvel agrégateur de type projet *(ProjectAggregator2.dll*) ainsi qu’un package Windows Install pour la redistribution *(ProjectAggregator2.msi*). Vous devez utiliser le nouvel agrégateur pour les types de projets gérés. ProjectAggregator2 travaille autour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des limitations de l’agrégateur de projet qui empêche les types de projets de code géré de fonctionner correctement. Les étapes suivantes décrivent comment modifier votre VSPackage pour utiliser le nouvel agrégateur.

1. Retirez le projet NativeHierarchyWrapper de votre solution.

2. Retirez les binaires NativeHierarchyWrapper de votre configuration.

3. Ajoutez *ProjectAggregator2.msi* à votre configuration.

---
title: Création et utilisation de stratégies d’archivage de l’analyse du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8e31ff799edc93d250eeeab57b349873a63ecf14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667710"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Création et utilisation de stratégies d’archivage de l’analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous utilisez Team Foundation Version Control (TFVC), vous pouvez créer une stratégie d’archivage de l’analyse du code pour les projets de code .NET Framework et natif (C/C++) dans un projet d’équipe. Vous pouvez utiliser la stratégie d’archivage de l’analyse du code pour contrôler et améliorer la qualité du code qui est archivé dans la base de code.

 La stratégie est passée lorsque la build locale est à jour et que l’analyse du code a été exécutée sur les fichiers sources les plus récents. Au minimum, les règles d’analyse du code qui sont activées dans le projet de code doivent contenir les mêmes règles que celles définies dans la stratégie d’archivage du projet d’équipe. Les règles qui ont été spécifiées en tant qu’erreurs dans les paramètres du projet d’équipe doivent également être spécifiées en tant qu’erreurs dans le projet de code

> [!IMPORTANT]
> Les stratégies d’archivage de l’analyse du code ne peuvent pas être appliquées aux projets de site Web. Ils peuvent être appliqués aux projets d’application Web.

 Vous créez des stratégies d’archivage de l’analyse du code à l’aide des paramètres de projet d’équipe de [!INCLUDE[esprscc](../includes/esprscc-md.md)] . Les stratégies d’archivage sont spécifiées et appliquées pour un projet d’équipe, mais les exécutions de l’analyse du code sont configurées et exécutées pour des projets de code individuels sur des ordinateurs de développement locaux. Cette section décrit comment spécifier des stratégies d’archivage de l’analyse du code pour un projet d’équipe et comment implémenter des stratégies d’analyse du code personnalisées pour le code managé.

## <a name="in-this-section"></a>Dans cette section
 [Comment : créer ou mettre à jour des stratégies d’archivage d’analyse du code standard](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md) Explique les étapes que vous utilisez pour définir et modifier une stratégie d’analyse du code pour un projet d’équipe.

 [Implémentation de stratégies d’archivage personnalisées pour le code managé](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md) Explique les étapes à suivre pour créer un ensemble de règles personnalisées pour la stratégie d’archivage d’un projet d’équipe, et pour synchroniser les projets de code du projet d’équipe avec la stratégie d’archivage.

 [Compatibilité des versions pour les stratégies d’archivage de l’analyse du code](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md) Explique les problèmes de compatibilité d’archivage de l’analyse du code entre les versions de [!INCLUDE[vstsLong](../includes/vstslong-md.md)] .

 [Comment : personnaliser le dictionnaire d’analyse du code](../code-quality/how-to-customize-the-code-analysis-dictionary.md) Explique comment ajouter des mots et des jetons au dictionnaire référencé dans les règles d’affectation de noms de l’analyse du code.

## <a name="related-sections"></a>Sections connexes
 [Définir et appliquer des niveaux de qualité](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)

 [Amélioration de la qualité du code avec les stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)

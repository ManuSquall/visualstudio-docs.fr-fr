---
title: 'Comment : configurer l’analyse du code pour un projet de code managé | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658858"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Procédure : configurer l’analyse du code pour un projet de code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] et [!INCLUDE[vsPro](../includes/vspro-md.md)] , vous pouvez choisir dans une liste d’ensembles de *règles* d’analyse du code à appliquer à un projet de code managé. L’ensemble de règles par défaut correspond aux règles Microsoft minimales recommandées. Vous pouvez appliquer un autre ensemble de règles à un projet ou à tous les projets d’une solution.

> [!NOTE]
> Pour plus d’informations sur la configuration d’un ensemble de règles pour les applications Web ASP.NET, consultez [Comment : configurer l’analyse du code pour une application web ASP.net](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Pour configurer un ensemble de règles pour un projet .NET Framework

1. Dans **Explorateur de solutions**, cliquez sur le projet.

2. Dans le menu **analyser** , cliquez sur **configurer l’analyse du code pour** *ProjectName*.

3. Dans les listes **configuration** et **plateforme** , cliquez sur la configuration de build et la plateforme cible.

4. Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, activez la case à cocher **activer l’analyse du code sur la build (définit CODE_ANALYSIS constante)** . Vous pouvez également exécuter l’analyse du code manuellement en ouvrant le menu **analyser** et en cliquant sur **exécuter l’analyse du code sur** *ProjectName*.

5. Par défaut, l'analyse du code ne signale pas d'avertissements pour le code généré automatiquement par les outils externes. Pour afficher les avertissements du code généré, désactivez la case à cocher **Supprimer les résultats du code généré** .

    > [!NOTE]
    > Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source pour un formulaire ou un modèle.

6. Dans la liste **exécuter cet ensemble de règles** , effectuez l’une des opérations suivantes :

    - Cliquez sur l’ensemble de règles que vous souhaitez utiliser.

    - Cliquez **\<Browse...>** pour spécifier un ensemble de règles personnalisées existant qui ne figure pas dans la liste.

    - Définissez un ensemble de règles personnalisé.

         Pour plus d’informations, consultez [création d’ensembles de règles personnalisées](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Voir aussi
 [Procédure pas à pas : configuration et utilisation d’un ensemble de règles personnalisé](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)

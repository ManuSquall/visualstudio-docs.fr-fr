---
title: 'Comment : configurer l’analyse du Code pour un projet de Code managé | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 98f3d14b73b0219d0fcec4312648bf613f37378e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239185"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Procédure : configurer l’analyse du code pour un projet de code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] et [!INCLUDE[vsPro](../includes/vspro-md.md)], vous pouvez choisir parmi une liste d’analyse du code *ensembles de règles* à appliquer à un projet de code managé. L’ensemble de règles par défaut est de règles Microsoft minimales recommandées. Vous pouvez appliquer un autre ensemble de règles à un projet ou à tous les projets dans une solution.  
  
> [!NOTE]
>  Pour plus d’informations sur la configuration d’un ensemble de règles pour les applications Web ASP.NET, consultez [Comment : configurer l’analyse du Code pour une Application Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Pour configurer un ensemble de règles pour un projet .NET Framework  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le projet.  
  
2.  Sur le **analyser** menu, cliquez sur **configurer l’analyse du Code pour** *nom_projet*.  
  
3.  Dans le **Configuration** et **plateforme** listes, cliquez sur la plateforme de configuration et la cible de génération.  
  
4.  Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, sélectionnez le **Enable Code Analysis sur la Build (définit la constante CODE_ANALYSIS)** case à cocher. Vous pouvez également exécuter manuellement l’analyse du code en ouvrant le **analyser** menu et en cliquant sur **exécuter l’analyse du Code sur** *nom_projet*.  
  
5.  Par défaut, l'analyse du code ne signale pas d'avertissements pour le code généré automatiquement par les outils externes. Pour afficher les avertissements du code généré, désactivez le **supprimer les résultats du code généré** case à cocher.  
  
    > [!NOTE]
    >  Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source pour un formulaire ou un modèle.  
  
6.  Dans le **exécuter cet ensemble de règles** liste, effectuez l’une des opérations suivantes :  
  
    -   Cliquez sur l’ensemble de règles que vous souhaitez utiliser.  
  
    -   Cliquez sur  **\<Parcourir... >** pour spécifier une règle personnalisée existante définie qui n’est pas dans la liste.  
  
    -   Définissez un ensemble de règles personnalisé.  
  
         Pour plus d’informations, consultez [création d’ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : configuration et utilisation d’un ensemble de règles personnalisé](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)




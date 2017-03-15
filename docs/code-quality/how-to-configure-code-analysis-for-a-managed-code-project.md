---
title: "Proc&#233;dure&#160;: configurer l’analyse du code pour un projet de code manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.csvb"
helpviewer_keywords: 
  - "analyse du code, sélectionner des ensembles de règles"
  - "analyse du code, ensemble de règles"
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 33
---
# Proc&#233;dure&#160;: configurer l’analyse du code pour un projet de code manag&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] et [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], vous pouvez sélectionner dans une liste d'analyse du code *rule sets* pour appliquer à un projet de code managé.  L'ensemble de règles par défaut s'intitule Règles Microsoft minimales recommandées.  Vous pouvez appliquer un autre ensemble de règles à un projet ou à tous les projets dans une solution.  
  
> [!NOTE]
>  Pour plus d'informations sur la configuration d'un ensemble de règles pour les applications Web ASP.NET, consultez [Comment : configurer l'analyse du code pour une application Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### Pour configurer un ensemble de règles pour un projet .NET Framework  
  
1.  Dans l'**Explorateur de solutions**, cliquez sur le projet.  
  
2.  Dans le menu **Analyser**, cliquez sur **Configurer l'analyse du code pour** *ProjectName*.  
  
3.  Dans les listes **Configuration** et **Plateforme**, cliquez sur la configuration de build et la plateforme cible.  
  
4.  Pour exécuter une analyse du code chaque fois que le projet est généré à l'aide de la configuration sélectionnée, activez la case à cocher **Activer l'analyse du code lors de la build \(définit la constante CODE\_ANALYSIS\)**.  Exécutez manuellement l'analyse du code en ouvrant le menu **Analyser** et en cliquant sur **Exécuter l'analyse du code sur** *ProjectName*.  
  
5.  Par défaut, l'analyse du code ne signale pas d'avertissements pour le code généré automatiquement par les outils externes.  Pour consulter les avertissements relatifs au code généré, désactivez la case à cocher **Supprimer les résultats du code généré**.  
  
    > [!NOTE]
    >  Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles.  Vous pouvez afficher et maintenir le code source pour un formulaire ou un modèle.  
  
6.  Dans la liste déroulante **Exécuter cet ensemble de règles**, effectuez l'une des opérations suivantes :  
  
    -   Cliquez sur l'ensemble de règles que vous voulez utiliser.  
  
    -   Cliquez sur **\<Parcourir…\>** pour spécifier un ensemble de règles personnalisé existant qui ne figure pas dans la liste.  
  
    -   Définissez un ensemble de règles personnalisé.  
  
         Pour plus d'informations, consultez [Création d'ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## Voir aussi  
 [Procédure pas à pas : configuration et utilisation d’un ensemble de règles personnalisé](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
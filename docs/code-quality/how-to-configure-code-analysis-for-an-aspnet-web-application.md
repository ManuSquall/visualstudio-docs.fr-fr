---
title: "Comment&#160;: configurer l&#39;analyse du code pour une application Web ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.asp"
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comment&#160;: configurer l&#39;analyse du code pour une application Web ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] et [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], vous pouvez choisir dans une liste des *ensembles de règles* d'analyse du code à appliquer à l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  L'ensemble de règles par défaut s'intitule Règles Microsoft minimales recommandées.  Vous pouvez sélectionner un autre ensemble de règles à appliquer au site Web.  
  
### Pour configurer un ensemble de règles pour un projet d'infrastructure de page ASP.NET  
  
1.  Sélectionnez le site Web dans l'**Explorateur de solutions**.  
  
2.  Dans le menu **Analyser**, cliquez sur **Configurer l'analyse du code pour le site Web**.  
  
3.  Si vous avez sélectionné la solution et que la solution comporte plusieurs projets, sélectionnez la configuration de build et le système d'exploitation cible dans les listes **Configuration** et **Plateforme**.  
  
4.  Pour chaque projet dans la solution, cliquez sur la colonne **Ensemble de règles**, puis sur le nom de l'ensemble de règles à exécuter.  
  
5.  Par défaut, l'analyse du code est exécutée sur tous les projets de la solution.  Pour désactiver ou activer l'analyse du code pour un projet particulier, procédez comme suit :  
  
    1.  Cliquez avec le bouton droit sur le nom du projet, puis cliquez sur Propriétés.  
  
    2.  Activez ou désactivez la case à cocher **Activer l'analyse du code**.  Vous pouvez également exécuter l'analyse du code manuellement en sélectionnant **Exécuter l'analyse du code sur le site Web** dans le menu **Analyser**.  
  
6.  Dans la liste déroulante **Exécuter cet ensemble de règles**, procédez comme suit :  
  
    -   Sélectionnez l'ensemble de règles que vous voulez utiliser.  
  
    -   Cliquez sur **\<Parcourir...\>** pour spécifier un ensemble de règles personnalisé existant qui ne figure pas dans la liste.  
  
    -   Définissez un ensemble de règles personnalisé.  Pour plus d'informations, consultez [Création d'ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md).
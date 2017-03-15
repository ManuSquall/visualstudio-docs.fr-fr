---
title: "Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, globalization"
  - "localization, Windows Forms"
  - "Windows Forms, localization"
  - "globalization, ClickOnce"
  - "satellite assemblies, ClickOnce"
  - "ClickOnce deployment, on-demand download"
  - "localization, ClickOnce deployment"
  - "ClickOnce deployment, localization"
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les applications Windows Forms peuvent être configurées pour plusieurs cultures à l’aide d’assemblys satellites. Un *assembly satellite* contient des ressources d’application pour une culture autre que la culture par défaut de l’application.  
  
 Comme indiqué dans la section [Localizing ClickOnce Applications](../deployment/localizing-clickonce-applications.md), vous pouvez inclure plusieurs assemblys satellites pour plusieurs cultures au sein du même déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Par défaut, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] télécharge tous les assemblys satellites de votre déploiement sur l’ordinateur client, même si un seul client n’a probablement besoin que d’un assembly satellite.  
  
 Cette procédure pas à pas explique comment marquer vos assemblys satellites comme facultatifs et télécharger uniquement l’assembly dont a besoin un ordinateur client pour ses paramètres de culture actuels. La procédure suivante utilise les outils disponibles dans le [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Vous pouvez également effectuer cette tâche dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Consultez également [Procédure pas à pas : téléchargement d’assemblys satellites à la demande avec l’API de déploiement ClickOnce à l’aide du concepteur](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) ou [Procédure pas à pas : téléchargement d’assemblys satellites à la demande avec l’API de déploiement ClickOnce à l’aide du concepteur](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  À des fins de test, l’exemple de code suivant affecte par programmation la valeur `ja-JP` à la culture. Consultez la section « Étapes suivantes » plus loin dans cette rubrique pour plus d’informations sur l’adaptation de ce code à un environnement de production.  
  
## Composants requis  
 Cette rubrique suppose que vous savez comment ajouter des ressources localisées à votre application à l’aide de Visual Studio. Pour obtenir des instructions détaillées, consultez [Procédure pas à pas : localisation de Windows Forms](https://msdn.microsoft.com/en-us/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### Pour télécharger des assemblys satellites à la demande  
  
1.  Ajoutez le code suivant à votre application pour activer le téléchargement à la demande des assemblys satellites.  
  
     [!code-cs[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2.  Générez des assemblys satellites pour votre application à l’aide de [Resgen.exe \(Resource File Generator\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Générez un manifeste d’application ou ouvrez votre manifeste d’application existant à l’aide de MageUI.exe. Pour plus d’informations sur cet outil, consultez [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  
  
4.  Cliquez sur l’onglet **Files**.  
  
5.  Cliquez sur le bouton d’**ellipse** \(**...**\) et sélectionnez le répertoire contenant tous les assemblys et fichiers de votre application, y compris les assemblys satellites que vous avez générés à l’aide de Resgen.exe. \(Le nom d’un assembly satellite se présente sous la forme *isoCode*\\ApplicationName.resources.dll, où *isoCode* est un identificateur de langue au format RFC 1766.\)  
  
6.  Cliquez sur **Populate** pour ajouter les fichiers à votre déploiement.  
  
7.  Cochez la case **Optional** pour chaque assembly satellite.  
  
8.  Définissez le champ de groupe pour chaque assembly satellite avec la valeur de son identificateur de langue ISO. Par exemple, pour un assembly satellite japonais, spécifiez le nom de groupe de téléchargement `ja-JP`. Cela permet au code ajouté à l’étape 1 de télécharger l’assembly satellite approprié, en fonction du paramètre de la propriété <xref:System.Threading.Thread.CurrentUICulture%2A> de l’utilisateur.  
  
## Étapes suivantes  
 Dans un environnement de production, vous aurez probablement besoin de supprimer la ligne dans l’exemple de code qui définit <xref:System.Threading.Thread.CurrentUICulture%2A> avec une valeur spécifique, car les ordinateurs clients ont la valeur correcte définie par défaut. Quand votre application s’exécute sur un ordinateur client japonais, par exemple, <xref:System.Threading.Thread.CurrentUICulture%2A> aura la valeur `ja-JP` par défaut. La définition par programmation de cette valeur est un bon moyen de tester vos assemblys satellites avant de déployer votre application.  
  
## Voir aussi  
 [Localizing ClickOnce Applications](../deployment/localizing-clickonce-applications.md)
---
title: "How to: Specify Verbose Log Files for ClickOnce Deployments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "logs, ClickOnce deployment"
  - "ClickOnce deployment, logging"
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Specify Verbose Log Files for ClickOnce Deployments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] maintient les fichiers journaux d'activité pour tous les déploiements.  Ces journaux documentent des détails se rapportant à l'installation, à l'initialisation, à la mise à jour et à la désinstallation d'un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Pour que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fournisse davantage de détails dans ces fichiers journaux, utilisez l'Éditeur du Registre \(**regedit.exe**\) pour spécifier le niveau de commentaires.  
  
> [!CAUTION]
>  L'utilisation incorrecte de l'Éditeur du Registre peut provoquer de sérieux problèmes qui peuvent nécessiter la réinstallation du système d'exploitation.  Utilisez\-le à vos risques et périls.  
  
 La procédure suivante décrit comment spécifier le niveau de commentaires pour les fichiers journaux [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour l'utilisateur actuel.  Pour réduire le niveau de commentaires, supprimez cette valeur de Registre.  
  
### Pour spécifier des fichiers journaux détaillés  
  
1.  Ouvrez **Regedit.exe**.  
  
2.  Naviguez jusqu'au nœud `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Si nécessaire, créez une nouvelle valeur de chaîne nommée `LogVerbosityLevel`.  
  
4.  Affectez à `LogVerbosityLevel` la valeur `1`.  
  
## Voir aussi  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)
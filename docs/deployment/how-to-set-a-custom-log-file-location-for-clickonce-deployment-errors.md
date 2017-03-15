---
title: "How to: Set a Custom Log File Location for ClickOnce Deployment Errors | Microsoft Docs"
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
  - "troubleshooting ClickOnce deployments"
  - "ClickOnce deployment, troubleshooting"
  - "ClickOnce deployment, error logging"
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Set a Custom Log File Location for ClickOnce Deployment Errors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] conserve des fichiers journaux d'activité pour tous les déploiements.  Ces journaux documentent toutes les erreurs relatives à l'installation et l'initialisation d'un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Par défaut, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crée un fichier journal pour chaque activation de déploiement.  Ces fichiers journaux sont stockés dans le dossier Temporary Internet Files.  Le fichier journal d'un déploiement est présenté à l'utilisateur lorsqu'un échec d'activation survient et que l'utilisateur clique sur **Détails** dans la boîte de dialogue d'erreur résultante.  
  
 Vous pouvez modifier ce comportement pour un client spécifique en utilisant l'Éditeur du Registre \(**regedit.exe**\) pour définir un chemin d'accès pour le fichier journal personnalisé.  Dans ce cas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consigne les réussites et les échecs de l'activation de tous les déploiements dans un seul fichier.  
  
> [!CAUTION]
>  L'utilisation incorrecte de l'Éditeur du Registre peut provoquer de sérieux problèmes qui peuvent nécessiter la réinstallation du système d'exploitation.  Utilisez\-le à vos risques et périls.  
  
> [!NOTE]
>  Vous devrez parfois tronquer ou supprimer le fichier journal pour l'empêcher de devenir trop volumineux.  
  
 La procédure suivante décrit comment définir un emplacement de fichier journal personnalisé pour un client particulier.  
  
### Pour définir un emplacement de fichier journal personnalisé  
  
1.  Ouvrez **Regedit.exe**.  
  
2.  Naviguez jusqu'au nœud `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Affectez à la valeur de chaîne `CheminFichierJournal` le chemin d'accès complet et le nom de fichier de votre emplacement de journal personnalisé favori.  
  
     Cet emplacement doit appartenir à un répertoire auquel l'utilisateur a un accès en écriture.  Par exemple, sous Windows Vista, créez la structure de dossier suivante et attribuez à `CheminFichierJournal` la valeur C:\\Users\\\<NomUtilisateur\>\\Documents\\Logs\\ClickOnce\\installation.log.  
  
## Voir aussi  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)
---
title: "How to: Specify a Start Menu Name for a ClickOnce Application | Microsoft Docs"
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
  - "Start menu resource name"
  - "Start menu name"
  - "ClickOnce deployment, Start menu name"
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# How to: Specify a Start Menu Name for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsqu'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est installée à la fois pour une utilisation en ligne et hors connexion, une entrée est ajoutée au menu **Démarrer** et à la liste **Ajout\/Suppression de programmes**.  Par défaut, le nom complet est identique au nom de l'assembly de l'application, mais vous pouvez modifier le nom complet en définissant **Nom du produit** dans la boîte de dialogue **Options de publication**.  
  
 Le **Nom du produit** s'affiche dans la page publish.htm ; pour une application hors ligne installée, il s'agit du nom de l'entrée qui apparaît dans le menu **Démarrer** et également du nom qui s'affiche dans **Ajout\/Suppression de programmes**.  
  
 Le **Nom de l'éditeur** apparaît dans la page publish.htm au\-dessus du **Nom du produit**, et pour une application hors ligne installée, il s'agit également du nom du dossier qui contient l'icône de l'application dans le menu **Démarrer**.  
  
 Vous pouvez définir les propriétés **Nom du produit** et **Nom de l'éditeur** dans la boîte de dialogue **Options de publication**, disponible dans la page **Publier** du **Concepteur de projets**.  
  
### Pour spécifier un nom de menu Démarrer  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Publier**.  
  
3.  Cliquez sur le bouton **Options** pour ouvrir la boîte de dialogue **Options de publication**.  
  
4.  Cliquez sur **Description**.  
  
5.  Dans la boîte de dialogue **Options de publication**, entrez le nom à afficher dans **Nom du produit**.  
  
6.  Vous pouvez éventuellement saisir un nom d'éditeur dans **Nom de l'éditeur**.  
  
## Voir aussi  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)
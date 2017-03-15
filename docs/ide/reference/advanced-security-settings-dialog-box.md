---
title: "Param&#232;tres de s&#233;curit&#233; avanc&#233;s, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.err.debug_in_zone_no_hostproc"
  - "vs.err.debug_in_zone_no_hostproc:11310"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Paramètres de sécurité avancés, boîte de dialogue"
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Param&#232;tres de s&#233;curit&#233; avanc&#233;s, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue vous permet de spécifier les paramètres de sécurité concernant le débogage dans la zone.  
  
 Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans l'**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**.  Lorsque le **Concepteur de projets** apparaît, cliquez sur l'onglet **Sécurité**.  Sur la page **Sécurité**, sélectionnez **Activer les paramètres de sécurité ClickOnce**, cliquez sur **Il s'agit d'une application de confiance partielle**, puis sur **Avancé**.  
  
## Liste UIElement  
 **Déboguer cette application à l'aide du jeu d'autorisations sélectionné**  
 Si vous activez cette case à cocher, le jeu d'autorisations sélectionné sur la page **Sécurité** est utilisé pendant le débogage.  Cette option est activée par défaut.  
  
 Pour que le débogage dans une zone de sécurité fonctionne, cette option ainsi que l'option **Activer le processus d'hébergement Visual Studio**, \(disponible sur la page **Déboguer** du **Concepteur de projets**\), doivent être activées.  
  
 Pour les projets d'application de navigateur Web WPF, l'option **Déboguer cette application à l'aide du jeu d'autorisations sélectionné** est activée et désactivée.  
  
 **Autorisez l'application à accéder à son site d'origine**  
 Si vous activez cette case à cocher, l'application peut accéder au site Web ou au partage serveur sur lequel il est publié.  Cette option est activée par défaut.  
  
 **Déboguez cette application comme si elle était téléchargée à partir de l'URL suivante :**  
 Si vous devez permettre à l'application d'accéder au site Web ou au partage serveur qui correspond à l'**URL d'installation** que vous avez spécifiée sur la page **Publier**, entrez cette URL ici.  Cette option est disponible uniquement lorsque l'option **Autoriser l'application à accéder à son site d'origine** est activée.  
  
## Voir aussi  
 [Page Sécurité, Concepteur de projets](../../ide/reference/security-page-project-designer.md)
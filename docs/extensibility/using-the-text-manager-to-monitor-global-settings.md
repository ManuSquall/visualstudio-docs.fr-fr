---
title: "Utilisation du Gestionnaire de texte pour surveiller les param&#232;tres globaux | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - analyser les paramètres globaux"
  - "éditeurs (Visual Studio SDK), hérités - Gestionnaire de texte"
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Utilisation du Gestionnaire de texte pour surveiller les param&#232;tres globaux
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous implémentez un éditeur principal, vous devez surveiller les modifications apportées aux paramètres globaux, car ces modifications peuvent affecter votre instance de l'éditeur.  Vous pouvez suivre les modifications en écoutant des événements déclenchés par le gestionnaire de texte.  Par exemple, lorsque vous spécifiez une préférence globale pour l'apparence ou le comportement d'un composant dans l'éditeur principal, comme son objet de données du document, les magasins de gestionnaire de texte ces informations et la communication à tous les clients affectés.  
  
## Fonctions de gestionnaire de texte  
 Le gestionnaire de texte déclenche des événements pour plusieurs paramètres, notamment :  
  
-   Si une mémoire tampon est sous contrôle de code source  
  
-   Procédure inscrire pour des notifications de changement de fichier  
  
-   Maintenez procédure que les vues sont associé à certaines mémoires tampons  
  
-   Texte les préférences de la colorisation  
  
-   Onglet et les préférences de l'espace  
  
 Les préférences spécifiques à une langue donnée ne sont pas gérées par le gestionnaire de texte.  Ces paramètres doivent être gérés par chaque service de langage.  
  
 La notification d'événements pour le gestionnaire de texte est fournie par l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> .  Implémentez cette interface sur votre objet client pour gérer des événements a déclenché le gestionnaire de texte.  Vous vous inscrivez à ces événements à l'aide de l'interface d' <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> dans le gestionnaire de texte.  
  
## Voir aussi  
 [Dans l'éditeur de base](../extensibility/inside-the-core-editor.md)   
 [Editor Features](http://msdn.microsoft.com/fr-fr/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
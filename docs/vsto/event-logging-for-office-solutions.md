---
title: "Journalisation des &#233;v&#233;nements pour les solutions Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "applications Office (développement Office dans Visual Studio), observateur d’événements"
  - "déploiement ClickOnce (développement Office dans Visual Studio), observateur d’événements"
  - "déploiement d’applications (développement Office dans Visual Studio), observateur d’événements"
  - "développement Office dans Visual Studio, observateur d’événements"
ms.assetid: 31a246fe-ce1c-4f0e-9a21-9cf974c247fe
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Journalisation des &#233;v&#233;nements pour les solutions Office
  Vous pouvez utiliser l’observateur d’événements de Windows pour consulter les messages d’exception capturés par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] lors de l’installation ou de la désinstallation de solutions Office. Vous pouvez utiliser ces messages du journal des événements pour résoudre les problèmes d’installation et de déploiement.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Lecture du journal des événements  
 Ouvrez l’**Observateur d’événements** et filtrez les événements que vous souhaitez afficher.  
  
#### Pour lire le journal des événements dans Windows Server 2003 et Windows XP  
  
1.  Dans le Panneau de configuration, ouvrez **Outils d’administration**.  
  
2.  Démarrez l’**Observateur d’événements**.  
  
3.  Dans la liste des journaux des événements, sélectionnez **Application**.  
  
4.  Dans le menu **Affichage**, cliquez sur **Filtrer**.  
  
5.  Dans la liste **Source d’événement**, sélectionnez **VSTO 4.0**.  
  
6.  Pour les événements d’installation, dans la zone **ID d’événement**, tapez **4096**.  
  
7.  Cliquez sur **OK** pour afficher la vue filtrée.  
  
#### Pour lire le journal des événements dans Windows 7, Windows Vista et Windows Server 2008  
  
1.  Dans le Panneau de configuration, ouvrez **Outils d’administration**.  
  
2.  Démarrez l’**Observateur d’événements**.  
  
3.  Développez **Journaux Windows**.  
  
4.  Dans la liste des journaux des événements, sélectionnez **Application**.  
  
5.  Dans le menu **Action**, cliquez sur **Filtrer le journal actuel**.  
  
6.  Dans la liste **Source d’événement**, sélectionnez **VSTO 4.0**.  
  
7.  Pour les événements d’installation, dans la zone **ID d’événement**, tapez **4096**.  
  
8.  Cliquez sur **OK** pour afficher la vue filtrée.  
  
 L’observateur d’événements fournit les informations suivantes :  
  
-   L’emplacement du manifeste de déploiement pour la solution.  
  
-   Un message qui décrit la cause de l’erreur ou de l’exception.  
  
 Ces messages d’exception peuvent vous aider à déterminer la cause d’un problème d’installation, tel qu’un certificat non approuvé, un emplacement de document non approuvé ou un manifeste de déploiement non valide.  
  
 Après la désinstallation d’une solution Office, les messages d’exception restent dans le journal des événements.  
  
 Pour afficher ou enregistrer les messages d’exception pendant l’exécution d’une solution Office, consultez [Débogage de projets Office](../vsto/debugging-office-projects.md) et [Débogage de projets Office](../vsto/debugging-office-projects.md).  
  
### Localisation  
 La langue du message d’exception est déterminée par la langue du runtime de Visual Studio Tools pour Office. Par exemple, si le module linguistique japonais est installé sur l’ordinateur de l’utilisateur final, le message d’exception est écrit dans le journal des événements en japonais.  
  
## Désactivation du journal des événements  
 Par défaut, le journal des événements est activé lorsque vous installez ou désinstallez des solutions Office. Vous pouvez désactiver le journal des événements en affectant la valeur « 1 » \(un\) à la variable d’environnement VSTO\_EVENTLOGDISABLED.  
  
#### Pour désactiver le journal des événements  
  
1.  Dans le Panneau de configuration, ouvrez **Système**.  
  
2.  Sous l'onglet **Avancé**, cliquez sur **Variables d'environnement**.  
  
3.  Dans le volet **Variables système**, cliquez sur **Nouveau**.  
  
4.  Dans la boîte de dialogue **Nouvelle variable système**, tapez **VSTO\_EVENTLOGDISABLED** dans la zone **Nom de la variable**.  
  
5.  Dans la zone **Valeur de la variable**, tapez **1**.  
  
6.  Cliquez sur **OK**.  
  
## Voir aussi  
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Dépannage du déploiement de solutions Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  
---
title: "How to: Specify the ClickOnce Offline or Online Install Mode | Microsoft Docs"
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
  - "ClickOnce deployment, specifying install mode"
  - "install mode"
  - "online applications"
  - "offline applications"
  - "ClickOnce install mode"
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Specify the ClickOnce Offline or Online Install Mode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'`Install Mode` d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] détermine si l'application sera disponible hors connexion ou en ligne.  Si vous choisissez **L'application est disponible en ligne uniquement**, l'utilisateur doit avoir accès à l'emplacement de publication [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] \(une page Web ou un partage de fichiers\) afin d'exécuter l'application.  Si vous choisissez **L'application est aussi disponible hors connexion**, l'application ajoute des entrées au menu **Démarrer** et à la boîte de dialogue **Ajouter ou supprimer des programmes** ; les utilisateurs peuvent exécuter l'application lorsqu'ils ne sont pas connectés.  
  
 Le `Install Mode` peut être défini dans la page **Publier** du **Concepteur de projets**.  
  
 **Remarque** Le `Install Mode` peut également être défini à l'aide de l'Assistant Publication.  Pour plus d'informations, consultez [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
### Pour rendre une application ClickOnce disponible en ligne uniquement  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Publier**.  
  
3.  Dans la zone **Mode et paramètres d'installation**, cliquez sur la case d'option **L'application est disponible en ligne uniquement**.  
  
### Pour rendre une application ClickOnce disponible en ligne ou hors connexion  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Publier**.  
  
3.  Dans la zone **Mode et paramètres d'installation**, cliquez sur la case d'option **L'application est également disponible hors connexion**.  
  
     Une fois installée, l'application ajoute des entrées au menu **Démarrer** et à la boîte de dialogue **Ajouter ou supprimer des programmes** du Panneau de configuration.  
  
## Voir aussi  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)
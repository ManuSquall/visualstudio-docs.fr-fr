---
title: "How to: Specify a Publish Page for a ClickOnce Application | Microsoft Docs"
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
  - "deploying applications [ClickOnce], specifying publish page"
  - "Publish Page property"
  - "publishing, ClickOnce"
  - "ClickOnce deployment, specifying publish page"
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# How to: Specify a Publish Page for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lors de la publication d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], une page Web par défaut \(publish.htm\) est générée et publiée avec l'application.  Cette page contient le nom de l'application, un lien permettant d'installer l'application et\/ou les composants requis éventuels, ainsi qu'un lien vers une rubrique d'aide qui décrit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  La propriété **Page de publication** de votre projet vous permet de spécifier un nom pour la page Web de votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Une fois la page de publication spécifiée, elle est copiée à l'emplacement de publication lors de sa prochaine publication, et n'est pas remplacée si vous la publiez à nouveau.  Si vous souhaitez personnaliser l'apparence de la page, vous pouvez le faire sans craindre de perdre vos modifications.  Pour plus d'informations, consultez [Comment : personnaliser la page web par défaut de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 La propriété **Page de publication** peut être définie dans la boîte de dialogue **Options de publication**, accessible à partir du volet **Publier** du **Concepteur de projets**.  
  
### Pour spécifier une page Web personnalisée pour une application ClickOnce  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Sélectionnez le volet **Publier**.  
  
3.  Cliquez sur le bouton **Options** pour ouvrir la boîte de dialogue **Options de publication**.  
  
4.  Cliquez sur **Déploiement**.  
  
5.  Dans la boîte de dialogue **Options de publication**, assurez\-vous que la case à cocher **Ouvrir la page Web de déploiement après la publication** est activée \(elle doit être sélectionnée par défaut\).  
  
6.  Dans la zone **Page Web de déploiement :**, entrez le nom de votre page Web, puis cliquez sur **OK**.  
  
### Pour empêcher le lancement de la page de publication à chaque publication  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Sélectionnez le volet **Publier**.  
  
3.  Cliquez sur le bouton **Options** pour ouvrir la boîte de dialogue **Options de publication**.  
  
4.  Cliquez sur **Déploiement**.  
  
5.  Dans la boîte de dialogue **Options de publication**, désactivez la case à cocher **Ouvrir la page Web de déploiement après la publication**.  
  
## Voir aussi  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [Comment : personnaliser la page web par défaut de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)
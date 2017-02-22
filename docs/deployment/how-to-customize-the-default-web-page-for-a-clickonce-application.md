---
title: "Comment&#160;: personnaliser la page Web par d&#233;faut d’une application ClickOnce | Microsoft Docs"
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
  - "Publish.htm, page web"
  - "déploiement ClickOnce, page web par défaut"
  - "déployer des applications (ClickOnce), publier"
  - "publier, ClickOnce"
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: personnaliser la page Web par d&#233;faut d’une application ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lors de la publication d'une application ClickOnce sur le Web, une page Web est générée automatiquement et publiée avec l'application.  La page par défaut contient le nom de l'application et des liens permettant de l'installer, d'installer les composants requis ou d'accéder à l'aide sur MSDN.  
  
> [!NOTE]
>  Les liens réellement visibles sur la page dépendent de l'ordinateur sur lequel vous la consultez et des composants requis que vous incluez.  
  
 Le nom par défaut de la page Web est Publish.htm ; vous pouvez le modifier dans le **Concepteur de projets**.  Pour plus d’informations, consultez [How to: Specify a Publish Page for a ClickOnce Application](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 La page Web Publish.htm est publiée uniquement si une version plus récente est détectée.  
  
> [!NOTE]
>  Les modifications que vous apportez à vos paramètres **Publier** n'affectent pas la page Publish.htm, à une exception près : si vous ajoutez ou supprimez des composants requis après la publication initiale, la liste de composants requis ne sera plus exacte.  Vous devrez modifier le texte du lien du composant requis pour refléter les modifications.  
  
### Pour personnaliser la page Web de publication  
  
1.  Publiez votre application ClickOnce sur un emplacement Web.  Pour plus d’informations, consultez [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
2.  Sur le serveur Web, ouvrez le fichier Publish.htm dans le Concepteurs Web Visual ou dans un autre éditeur HTML.  
  
3.  Personnalisez la page comme vous le souhaitez et enregistrez\-la.  
  
4.  Optionnel.  Afin d'empêcher Visual Studio de remplacer votre page Web de publication personnalisée, désactivez **Générer automatiquement la page Web de déploiement après chaque publication** dans la boîte de dialogue Options de publication.  
  
## Voir aussi  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Install Prerequisites with a ClickOnce Application](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [How to: Specify a Publish Page for a ClickOnce Application](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
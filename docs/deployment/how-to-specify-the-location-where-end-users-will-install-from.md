---
title: "How to: Specify the Location Where End Users Will Install From | Microsoft Docs"
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
  - "deploying applications [ClickOnce], specifying an installation URL"
  - "URLs, specifying an installation URL"
  - "installation, specifying installation an URL"
  - "Installation URL property"
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Specify the Location Where End Users Will Install From
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lors de la publication d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], l'emplacement auquel les utilisateurs doivent accéder pour télécharger et installer l'application n'est pas nécessairement l'emplacement dans lequel vous avez initialement publié l'application.  Par exemple, dans certaines organisations, un développeur peut publier une application sur un serveur intermédiaire, puis un administrateur peut la déplacer vers un serveur Web.  
  
 Dans ce cas, vous pouvez utiliser la propriété `Installation URL` pour spécifier le serveur Web sur lequel les utilisateurs doivent se rendre pour télécharger l'application.  Cette opération est nécessaire pour que le manifeste d'application sache où rechercher des mises à jour.  
  
 La propriété `Installation URL` peut être définie dans la page **Publier** du **Concepteur de projets**.  
  
 **Remarque** La propriété `Installation URL` peut également être définie à l'aide de l'**Assistant Publication**.  Pour plus d'informations, consultez [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
### Pour spécifier une URL d'Installation  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Publier**.  
  
3.  Dans le champ URL d'installation, entrez l'emplacement d'installation à l'aide d'une URL qualifiée complète au format http:\/\/www.microsoft.com\/NomApplication, ou d'un chemin UNC au format \\\\Serveur\\NomApplication.  
  
## Voir aussi  
 [How to: Specify Where Visual Studio Copies the Files](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)
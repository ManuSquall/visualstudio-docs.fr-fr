---
title: "Cr&#233;ation de contr&#244;les r&#233;utilisables pour les composants WebPart ou les pages d&#39;application | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, contrôles utilisateur"
  - "contrôles utilisateur (développement SharePoint dans Visual Studio), créer"
ms.assetid: 8fcafd98-c002-47f1-b4a9-cbb500232616
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Cr&#233;ation de contr&#244;les r&#233;utilisables pour les composants WebPart ou les pages d&#39;application
  Dans Visual Studio, vous pouvez créer des contrôles personnalisés et réutilisables qui peuvent être consommés par des pages d'application et des composants WebPart qui s'exécutent dans SharePoint.  Ces contrôles sont appelés contrôles utilisateur.  Pour plus d'informations sur les contrôles utilisateur, consultez [ASP.NET User Controls](http://msdn.microsoft.com/library/5e601b3d-bb16-4dbe-9e35-7e92a34565ca).  
  
## Création d'un contrôle utilisateur  
 Pour créer un contrôle utilisateur, ajoutez un **Contrôle utilisateur** à un **Projet SharePoint vide**.  Pour plus d'informations, consultez [Comment : créer un contrôle utilisateur pour un composant WebPart ou une page d'application SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Lorsque vous ajoutez un élément **Contrôle utilisateur**, Visual Studio crée un dossier dans votre projet, puis ajoute plusieurs fichiers au dossier.  Le tableau suivant décrit chaque fichier.  
  
|Fichier|Description|  
|-------------|-----------------|  
|Fichier du contrôle utilisateur|Définit le contrôle utilisateur.  Vous pouvez concevoir le contrôle utilisateur en ajoutant des contrôles et du balisage à ce fichier.|  
|Fichier de code|Contient le code\-behind du contrôle utilisateur.  Vous pouvez ajouter du code à ce fichier pour gérer des événements.|  
|Fichier de code du concepteur|Contient le code généré par le concepteur. Ne doit pas être modifié directement.|  
  
## Conception du contrôle utilisateur  
 Vous pouvez concevoir le contrôle utilisateur à l'aide du concepteur Visual Web Developer dans Visual Studio.  Ce concepteur s'affiche lorsque vous ouvrez le fichier du contrôle utilisateur dans votre projet et cliquez sur l'onglet de **Conception**.  Pour plus d'informations sur l'utilisation de ce concepteur, consultez [Visual Studio Web Development Content Map](http://msdn.microsoft.com/fr-fr/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
## Consommation du contrôle utilisateur  
 Les contrôles utilisateur ne s'affichent pas dans SharePoint tant que vous ne les avez pas inclus dans une page d'application ou un composant WebPart.  
  
 Pour inclure un contrôle utilisateur dans une page d'application, ajoutez une directive [@ Register](http://msdn.microsoft.com/fr-fr/66f34922-be41-4e36-9dc8-1774d85311d1) à la page d'application, puis déclarez le contrôle utilisateur dans un ou plusieurs espaces réservés de contenu dans la page.  Pour obtenir un exemple de réalisation de cette tâche dans une page Web ASP.NET standard, consultez [How to: Include a User Control in an ASP.NET Web Page](http://msdn.microsoft.com/library/7c3bfd74-846c-4b88-b1ef-45d75860af92).  
  
 Pour inclure un contrôle utilisateur dans un composant WebPart, ajoutez le contrôle utilisateur à la collection <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> du composant WebPart, dans le fichier de code de ce composant WebPart.  L'exemple suivant ajoute un contrôle utilisateur à la collection <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> d'un composant WebPart.  
  
 [!code-csharp[SP_VisualWebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1.cs#5)]
 [!code-vb[SP_VisualWebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1.vb#5)]  
  
## Débogage d'un contrôle utilisateur  
 Pour déboguer un contrôle utilisateur, vérifiez que le contrôle utilisateur est inclus dans une page d'application ou un composant WebPart dans votre projet SharePoint.  Vous pouvez ensuite déboguer le code dans le contrôle utilisateur de la même manière que vous le feriez dans tout projet Visual Studio.  
  
 Lorsque vous démarrez le débogueur Visual Studio, Visual Studio ouvre le site SharePoint.  
  
 Dans SharePoint, ouvrez la page d'application qui inclut le contrôle utilisateur.  Si le contrôle utilisateur est inclus dans un composant WebPart, ajoutez le composant WebPart à une page de composant WebPart dans SharePoint.  
  
 Pour plus d'informations sur le débogage de projets SharePoint, consultez [Dépannage des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : créer un contrôle utilisateur pour un composant WebPart ou une page d'application SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Explique comment créer des contrôles personnalisés et réutilisables qui peuvent être utilisés par des pages d'application et des composants WebPart s'exécutant dans SharePoint.|  
|[Utilisation de Visual Web Developer](http://msdn.microsoft.com/fr-fr/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Explique comment utiliser le concepteur qui s'affiche lorsque vous ouvrez une page Web dans votre projet.|  
  
  
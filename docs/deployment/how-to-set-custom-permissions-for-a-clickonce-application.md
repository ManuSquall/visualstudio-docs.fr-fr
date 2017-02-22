---
title: "Comment&#160;: d&#233;finir des autorisations personnalis&#233;es pour une application ClickOnce | Microsoft Docs"
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
  - "applications ClickOnce, autorisations"
  - "autorisations, applications ClickOnce"
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: d&#233;finir des autorisations personnalis&#233;es pour une application ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez déployer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui utilise les autorisations par défaut pour la zone Internet ou Intranet local. Vous pouvez également créer une zone personnalisée pour les autorisations spécifiques nécessaires à l’application. Vous pouvez pour cela personnaliser les autorisations de sécurité dans la page **Sécurité** du **Concepteur de projets**.  
  
### Pour personnaliser une autorisation  
  
1.  Après avoir sélectionné un projet dans l’**Explorateur de solutions**, dans le menu **Projet**, cliquez sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Sécurité**.  
  
3.  Cochez la case **Activer les paramètres de sécurité ClickOnce**.  
  
4.  Sélectionnez la case d’option **Il s’agit d’une application de confiance partielle**.  
  
     Les contrôles de la section **Autorisations de sécurité ClickOnce** sont activés.  
  
5.  Dans la liste déroulante **Zone à partir de laquelle votre application sera installée**, cliquez sur **\(Personnalisé\)**.  
  
6.  Cliquez sur **Modifier les autorisations XML**.  
  
     Le fichier app.manifest s’ouvre dans l’éditeur XML.  
  
7.  Avant l’élément `</applicationRequestMinimum>`, ajoutez le code XML pour les autorisations dont votre application a besoin.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la méthode `ToXml` d’un jeu d'autorisations pour générer le code XML du manifeste d’application. Par exemple, pour générer le code XML pour le jeu d’autorisations <xref:System.Security.Permissions.EnvironmentPermission>, appelez la méthode <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A>. Pour plus d’informations sur la structure du code XML de jeu d’autorisations, consultez [NIB: Comment : importer un jeu d’autorisations à l’aide d’un fichier XML](http://msdn.microsoft.com/fr-fr/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## Voir aussi  
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d'accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)
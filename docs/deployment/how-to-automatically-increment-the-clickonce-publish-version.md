---
title: "How to: Automatically Increment the ClickOnce Publish Version | Microsoft Docs"
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
  - "deploying applications [ClickOnce], incrementing publish version automatically"
  - "Publish Version property, incrementing"
  - "ClickOnce deployment, incrementing publish version automatically"
  - "publishing, ClickOnce"
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Automatically Increment the ClickOnce Publish Version
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lors de la publication d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la modification de la propriété `Publish Version` entraîne la publication de l'application en tant que mise à jour.  Par défaut, Visual Studio incrémente automatiquement le nombre `Revision` du `Publish Version` à chaque publication de l'application.  
  
 Vous pouvez désactiver ce comportement dans la page **Publier** du **Concepteur de projets**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour désactiver l'incrémentation automatique de la version de publication  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Publier**.  
  
3.  Dans la section **Version de publication**, désactivez la case à cocher **Incrémenter automatiquement la révision avec chaque version**.  
  
## Voir aussi  
 [How to: Set the ClickOnce Publish Version](../Topic/How%20to:%20Set%20the%20ClickOnce%20Publish%20Version.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)
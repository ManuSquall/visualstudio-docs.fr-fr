---
title: "How to: Change the Publish Language for a ClickOnce Application | Microsoft Docs"
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
  - "Publish language property"
  - "ClickOnce deployment, changing publish language"
  - "publishing, ClickOnce"
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# How to: Change the Publish Language for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lors de la publication d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], l'interface utilisateur affichée pendant l'installation est par défaut celle de la langue et de la culture de votre ordinateur de développement.  Si vous publiez une application traduite, vous devez spécifier une langue et une culture correspondant à la version traduite.  Celles\-ci sont déterminées par la propriété `Publish language` de votre projet.  
  
 La propriété `Publish language` peut être définie dans la boîte de dialogue **Options de publication**, disponible dans la page **Publier** du **Concepteur de projets**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour modifier la langue de publication  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Publier**.  
  
3.  Cliquez sur le bouton **Options** pour ouvrir la boîte de dialogue **Options de publication**.  
  
4.  Cliquez sur **Description**.  
  
5.  Dans la boîte de dialogue **Options de publication**, sélectionnez une langue et une culture dans la liste déroulante **Langue de publication**, puis cliquez sur **OK**.  
  
## Voir aussi  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)
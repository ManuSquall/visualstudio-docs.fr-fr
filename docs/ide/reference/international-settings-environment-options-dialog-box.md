---
title: "Param&#232;tres internationaux, Environnement, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.InternationalSettings"
  - "VS.ToolsOptionsPages.Environment.International_Settings"
  - "VS.Environment.International Settings"
  - "VS.ToolsOptionsPag.Environment.International_Settings"
helpviewer_keywords: 
  - "Paramètres internationaux (boîte de dialogue)"
  - "langages, paramètres d’environnement"
  - "Options (boîte de dialogue), paramètres internationaux"
  - "langages, spécification du langage par défaut"
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Param&#232;tres internationaux, Environnement, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La page Paramètres internationaux vous permet de changer la langue par défaut quand vous avez plusieurs versions linguistiques de l'environnement de développement intégré \(IDE\) installé sur votre ordinateur.  Vous pouvez accéder à cette boîte de dialogue en sélectionnant **Options** dans le menu **Outils**, puis en choisissant **Paramètres internationaux** dans le dossier **Environnement**.  Si cette page n'apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.  
  
> [!NOTE]
>  Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Langue**  
 Répertorie les langues disponibles pour les versions linguistiques du produit installé.  Cette option n'est disponible que si vous avez plusieurs versions linguistiques installées sur votre ordinateur.  Si plusieurs versions linguistiques de produits ou si une installation mixte de versions linguistiques de produits partagent le même environnement, la langue sélectionnée est changée en **Identique à Microsoft Windows**.  
  
> [!CAUTION]
>  Dans un système où plusieurs langues sont installées, les outils de génération Visual C\+\+ \(cl.exe, link.exe, nmake.exe, bscmake.exe et les fichiers associés\) ne sont pas affectés par ce paramètre.  Ces outils utilisent la version pour la dernière langue installée, et les outils pour la langue précédemment installée sont remplacés, car les outils de génération Visual C\+\+ n'utilisent pas le modèle de DLL satellite.  
  
## Voir aussi  
 [Installation de versions multilingues de Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)
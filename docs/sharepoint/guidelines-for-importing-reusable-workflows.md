---
title: "Directives pour l&#39;importation de flux de travail r&#233;utilisables | Microsoft Docs"
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
  - "importer des éléments (développement SharePoint dans Visual Studio)"
  - "flux de travail réutilisables (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, importer des éléments"
  - "développement SharePoint dans Visual Studio, flux de travail réutilisables"
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Directives pour l&#39;importation de flux de travail r&#233;utilisables
  Pour importer des flux de travail réutilisables qui ont été créés dans SharePoint Designer, utilisez le modèle de projet SharePoint 2010 Importer le flux de travail réutilisable dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Ce modèle importe un *flux de travail* *déclaratif* \(en [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] uniquement\) et le convertit en *flux de travail avec code*, qui est un flux de travail pouvant être amélioré avec du code [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)].  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Procédure pas à pas : importation d'un flux de travail réutilisable de SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Toutefois, le modèle Importer SharePoint 2010 le flux de travail réutilisable permet d'importer uniquement des solutions de batterie.  Si vous souhaitez déployer votre flux de travail en tant que solution bac à sable \(sandbox\), importez\-le avec le modèle Importer le package de solution SharePoint 2010.  Toutefois, en procédant ainsi, vous ne pourrez pas le convertir en flux de travail avec code ni le modifier en tant que tel.  
  
## Importation de flux de travail réutilisables à l'aide du modèle Importer le flux de travail réutilisable  
 Si vous importez un flux de travail réutilisable à l'aide du modèle SharePoint 2010 Importer le flux de travail réutilisable, vous pourrez exécuter ou modifier la solution comme toute autre solution SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], mais vous devrez peut\-être corriger manuellement certains éléments.  
  
### Importation de formulaires de tâche  
 Le modèle de projet SharePoint 2010 Importer le flux de travail réutilisable permet d'importer tous les formulaires d'initiation et d'association ; en revanche, il n'importe qu'un seul formulaire de tâche car le schéma du flux de travail avec code n'autorise qu'un seul formulaire de ce type.  Tout formulaire de tâche supplémentaire de la solution de flux de travail d'origine est placé dans le dossier **Autres fichiers importés** de l'**Explorateur de solutions**.  
  
## Importation de flux de travail réutilisables à l'aide du modèle Importer le package de solution SharePoint 2010  
 Si vous importez un flux de travail réutilisable à l'aide du modèle Importer le package de solution SharePoint 2010, vous devez tenir compte des points suivants :  
  
-   Après avoir importé le flux de travail, vous pouvez immédiatement le déployer et l'exécuter dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en appuyant sur F5.  Toutefois, si vous modifiez de quelque manière que ce soit le flux de travail dans la solution importée, vous devrez peut\-être corriger manuellement des éléments du projet pour pouvoir déployer et exécuter le flux de travail.  
  
-   Étant donné que le flux de travail est déclaratif, vous ne pouvez pas lui ajouter de code.  Pour convertir le flux de travail en flux de travail avec code, vous devez l'importer dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] à l'aide du modèle SharePoint 2010 Importer le flux de travail réutilisable.  
  
-   Bien que vous puissiez modifier le fichier du concepteur de workflow \(.xoml\) en mode Design, il est recommandé d'effectuer cette opération en mode Source car le concepteur de workflow affiche à tort des erreurs.  
  
-   Le débogage ne fonctionne pas dans le flux de travail pour le contenu déclaratif.  Les points d'arrêt définis dans [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] ne sont pas atteints.  
  
## Importation de solutions de flux de travail globalement réutilisables  
 Les flux de travail globalement réutilisables ne peuvent pas être importés à l'aide du modèle SharePoint 2010 Importer le flux de travail réutilisable.  Pour importer un flux de travail globalement réutilisable, vous devez le convertir en flux de travail qui n'est pas globalement réutilisable ou utiliser le modèle Importer le package de solution SharePoint 2010.  
  
 Pour convertir le flux de travail, créez une copie du flux de travail globalement réutilisable dans SharePoint Designer \(en ouvrant le menu de raccourci du flux de travail et en sélectionnant **Enregistrer en tant que copie**\).  Importez ensuite le nouveau flux de travail réutilisable avec le modèle SharePoint 2010 Importer le flux de travail réutilisable dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Pour importer le flux de travail globalement réutilisable sans le modifier, utilisez le modèle Importer le package de solution SharePoint.  Si vous utilisez cette méthode, le flux de travail n'est pas converti en flux de travail avec code et reste un flux de travail déclaratif.  
  
## Voir aussi  
 [Importation d'éléments d'un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Procédure pas à pas : importation d'un flux de travail réutilisable de SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  
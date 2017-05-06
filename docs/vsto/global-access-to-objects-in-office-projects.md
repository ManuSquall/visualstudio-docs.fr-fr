---
title: "Acc&#232;s global aux objets dans les projets Office"
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
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "Globals (classe), accès global aux objets"
  - "feuilles de calcul (développement Office dans Visual Studio), accès global"
  - "documents (développement Office dans Visual Studio), accès global"
  - "gestionnaires d'événements (développement Office dans Visual Studio)"
  - "ThisWorkbook_Startup"
  - "compléments d'application (développement Office dans Visual Studio)"
  - "compléments (développement Office dans Visual Studio), événements"
  - "classeurs (développement Office dans Visual Studio), accès global"
  - "ThisWorkbook_Shutdown"
  - "personnalisations au niveau du document (développement Office dans Visual Studio)"
  - "Startup (événement)"
  - "Shutdown (événement)"
  - "projets (développement Office dans Visual Studio), accès global"
  - "documents Office (développement Office dans Visual Studio), accès global"
  - "ThisAddin_Startup"
  - "événements (développement Office dans Visual Studio)"
  - "ThisAddIn_Shutdown"
ms.assetid: f6a7f0ef-75d0-4a9b-9aec-be95ffa26adf
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Acc&#232;s global aux objets dans les projets Office
  Lorsque vous créez un projet Office, Visual Studio génère automatiquement une classe nommée `Globals` dans le projet. Vous pouvez utiliser la classe `Globals` pour accéder à plusieurs éléments de projet différents au moment de l'exécution à partir du code du projet.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Utilisation de la classe Globals  
 `Globals` est une classe statique qui conserve les références à certains éléments de votre projet. Grâce à la classe `Globals`, vous pouvez accéder aux éléments suivants à partir de tout code de votre projet au moment de l'exécution :  
  
-   Classes `ThisWorkbook` et `Sheet`*n* dans un projet de modèle ou un classeur Excel. Vous pouvez accéder à ces objets à l'aide des propriétés `Globals.ThisWorkbook` et `Sheet`*n*.  
  
-   Classe `ThisDocument` dans un projet de modèle ou un document Word. Vous pouvez accéder à cet objet à l'aide de la propriété `Globals.ThisDocument`.  
  
-   Classe `ThisAddIn` dans un projet de complément VSTO. Vous pouvez accéder à cet objet à l'aide de la propriété `Globals.ThisAddIn`.  
  
-   Tous les rubans de votre projet que vous avez personnalisés en utilisant le Concepteur de ruban. Vous pouvez accéder aux rubans à l'aide de la propriété `Globals.Ribbons`. Pour plus d'informations, consultez [Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md).  
  
-   Toutes les zones de formulaire Outlook dans un projet de complément VSTO Outlook. Vous pouvez accéder aux zones de formulaire à l'aide de la propriété `Globals.FormRegions`. Pour plus d'informations, consultez [Accès à une zone de formulaire au moment de l'exécution](../vsto/accessing-a-form-region-at-run-time.md).  
  
-   Un objet de fabrique qui vous permet de créer des contrôles de ruban et des éléments hôtes au moment de l'exécution dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Vous pouvez accéder à cet objet à l'aide de la propriété `Globals.Factory`. Cet objet est une instance d'une classe qui implémente l'une des interfaces suivantes :  
  
    -   <xref:Microsoft.Office.Tools.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
 Par exemple, vous pouvez utiliser la propriété `Globals.Sheet1` pour insérer le texte dans un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> sur `Sheet1` lorsqu'un utilisateur clique sur un bouton du volet Actions dans un projet de niveau document pour Excel.  
  
 [!code-csharp[Trin_VstcoreProgramming#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstcoreProgramming#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#1)]  
  
## Initialisation de la classe Globals  
 Le code qui tente d’utiliser la classe `Globals` avant la fin de l’initialisation totale du document ou du complément VSTO peut lever une exception au moment de l’exécution. Par exemple, l'utilisation de `Globals` lors de la déclaration d'une variable au niveau de la classe peut échouer, car la classe `Globals` peut ne pas être initialisée avec des références à tous les éléments hôtes avant l'instanciation de l'objet déclaré.  
  
> [!NOTE]  
>  La classe `Globals` n'est jamais initialisée au moment du design, mais des instances de contrôle sont créées par le concepteur. Cela signifie que si vous créez un contrôle utilisateur qui utilise une propriété de la classe `Globals` depuis l'intérieur d'une classe de contrôle utilisateur, vous devez spécifier si la propriété doit retourner **null** avant d'essayer d'utiliser l'objet retourné.  
  
## Voir aussi  
 [Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Accès à une zone de formulaire au moment de l'exécution](../vsto/accessing-a-form-region-at-run-time.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Élément hôte de document](../vsto/document-host-item.md)   
 [Élément hôte de classeur](../vsto/workbook-host-item.md)   
 [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)   
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)  
  
  
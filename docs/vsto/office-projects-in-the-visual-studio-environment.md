---
title: "Projets Office dans l&#39;environnement Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.WordDocument"
  - "VST.ProjectItem.ExcelWorkbook"
  - "VST.ProjectItem.ExcelTemplate"
  - "VST.ProjectItem.ExcelSheet"
  - "VST.ProjectItem.BlueprintCode"
  - "VST.ProjectItem.Word"
  - "VST.ProjectItem.Excel"
  - "VST.ProjectItem.AddinProject"
  - "Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner"
  - "VST.ProjectItem.ExtendedBluePrint"
  - "VST.ProjectItem.WordTemplate"
  - "Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner"
  - "VST.Designer.ExcelVST.Designer.Word"
  - "VST.ProjectItem.ExtendedBlueprintCode"
  - "VST.ProjectItem.BluePrint"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "documents (développement Office dans Visual Studio)"
  - "fichiers masqués (développement Office dans Visual Studio)"
  - "fichiers projet (développement Office dans Visual Studio), masqués"
  - "développement Office dans Visual Studio, documents dans Visual Studio"
  - "mode Design, Excel"
  - "concepteurs, développement Office dans Visual Studio"
  - "documents Office (développement Office dans Visual Studio)"
  - "documents Office (développement Office dans Visual Studio), à propos des documents dans Visual Studio"
  - "concepteurs (développement Office dans Visual Studio)"
  - "Concepteur Word"
  - "Word (développement Office dans Visual Studio), concepteur Word"
  - "Visual Studio, documents Office dans"
  - "feuilles de calcul (développement Office dans Visual Studio)"
  - "VST.Designer.ExcelVST.Designer.Word"
ms.assetid: 4bff36c9-4edd-4b28-89e6-0ea9f6caca02
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Projets Office dans l&#39;environnement Visual Studio
  En termes de développement, les projets Microsoft Office offrent une expérience similaire à d'autres types de projets dans Visual Studio, tels que les projets Windows Forms. Lorsque vous créez ou ouvrez un projet Office, les éléments de projet s'affichent dans l'**Explorateur de solutions**. Pour les projets au niveau du document, le document \(le document Word ou le classeur Excel\) s'ouvre dans Visual Studio et se comporte comme un concepteur visuel.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Éléments de projet dans l'Explorateur de solutions  
 Dans un projet au niveau du document, l'**Explorateur de solutions** affiche les éléments par défaut suivants :  
  
-   Nœuds du document, du classeur et des feuilles de calcul qui sont personnalisés par le projet. Ces nœuds servent de conteneurs aux fichiers de code associés au document, au classeur et aux feuilles.  
  
-   Fichiers de code associés au document, classeur et feuilles de calcul personnalisés par le projet. Dans les projets Word, les fichiers de code sont associés au modèle ou au document Word. Dans les projets Excel, les fichiers de code sont associés au modèle ou au classeur Excel, et à chaque feuille de calcul et feuille de graphique dans le classeur ou le modèle.  
  
-   Des fichiers projet masqués que vous ne pouvez pas modifier directement. Pour plus d'informations, consultez [Fichiers projet masqués](#hiddenfiles).  
  
 Dans un projet de complément VSTO, l’**Explorateur de solutions** affiche les éléments par défaut suivants :  
  
-   Le nœud d'application. Ce nœud a le même nom que l'application hôte, par exemple **Word**, **Excel** ou **Outlook**. Le nœud d'application contient le fichier de code ThisAddIn. Il fournit également la propriété **Espace de noms de l'élément hôte**. Pour plus d’informations sur cette propriété, consultez [Propriétés dans les projets Office](../vsto/properties-in-office-projects.md).  
  
-   Le fichier de code ThisAddIn. Ce fichier contient la classe `ThisAddIn` générée pour votre complément VSTO. Pour plus d’informations sur cette classe, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Des fichiers projet masqués que vous ne pouvez pas modifier directement. Pour plus d'informations, consultez [Fichiers projet masqués](#hiddenfiles).  
  
### Certificats temporaires  
 Les projets Office incluent également un certificat temporaire nommé *nom\_projet*\_TemporaryKey.pfx. Ce certificat est utilisé pour signer les manifestes de déploiement et d'application du projet pendant le développement. Pour plus d’informations, consultez [Octroi de niveaux de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md) et [Sécurisation des solutions Office](../vsto/securing-office-solutions.md).  
  
###  <a name="hiddenfiles"></a> Fichiers projet masqués  
 Plusieurs fichiers projet sont masqués par défaut. Ces fichiers sont générés par Visual Studio et ils diffèrent par type de projet. Pour afficher les fichiers masqués, cliquez sur **Afficher tous les fichiers** dans l'**Explorateur de solutions**.  
  
 Ne modifiez pas les fichiers projet masqués. La modification directe de ces fichiers n'est pas prise en charge et peut endommager votre projet. Les fichiers projet masqués sont régénérés à chaque fois que certaines modifications sont effectuées dans le document. Si vous apportez des modifications manuelles à un fichier projet masqué, ces modifications seront perdues lorsque le fichier sera régénéré.  
  
## Concepteur de documents dans les projets au niveau du document  
 Les projets au niveau du document pour Excel et Word fournissent un concepteur qui héberge le document associé à votre projet dans Visual Studio. Ce concepteur vous permet de modifier le document sans avoir à sortir de l'environnement Visual Studio.  
  
 Pour ouvrir un document dans le concepteur, double\-cliquez sur le fichier de code dans l'**Explorateur de solutions** associé au document. Par exemple, pour ouvrir la feuille de calcul **Feuille1** dans le concepteur dans un projet Excel, double\-cliquez sur le fichier de code **Feuille1**.  
  
 Lorsque vous modifiez le document dans le concepteur, vous pouvez tirer parti des fonctionnalités natives de l'application Office. Par exemple, vous pouvez taper le texte dans le document ou dans une feuille de calcul, ou vous pouvez utiliser le ruban pour effectuer des tâches telles qu'ajouter une table ou un graphique. Par défaut, le mappage des raccourcis clavier prend la valeur par défaut du mappage Visual Studio. Pour utiliser à la place les mappages des raccourcis clavier Office, modifiez les paramètres sous le nœud **Paramètres du clavier Microsoft Office** dans la boîte de dialogue **Options** du menu **Outils**.  
  
### Contrôles dans des documents  
 Vous pouvez faire glisser des *contrôles hôtes* et des contrôles Windows Forms de la **Boîte à outils** Visual Studio sur l'aide de conception du document. Les contrôles hôtes sont des versions spécialisées d'objets Office, tels que les contrôles de contenu Word et les plages Excel, qui peuvent être utilisés dans les projets Office créés à l'aide de Visual Studio. Les contrôles hôtes ont des fonctionnalités supplémentaires qui ne sont pas disponibles dans les objets Office correspondants, comme la liaison de données et les événements supplémentaires.  
  
 Pour plus d’informations, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md) et [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
### Feuilles de calcul et classeurs Excel dans le concepteur  
 Lorsque vous ouvrez une feuille de calcul dans le concepteur, vous pouvez la modifier de la même façon que lorsque vous l'ouvrez directement dans Excel. Si vous double\-cliquez sur une cellule de la feuille de calcul, la cellule passe en mode édition. Si vous double\-cliquez sur une cellule qui contient un contrôle hôte, l'éditeur de code s'ouvre et Visual Studio génère le gestionnaire d'événements par défaut pour le contrôle. Pour naviguer jusqu'à d'autres feuilles de calcul, vous pouvez cliquer sur les onglets de feuille de calcul en bas de concepteur.  
  
 Lorsque vous ouvrez le classeur dans le concepteur, il n'y a aucune aire de conception. Le mode Design du classeur consiste en une grande barre d'état des composants qui remplit le concepteur.  
  
 Le classeur et chaque feuille qu'il contient ont un fichier de code associé. Chaque fichier de code contient une classe d'*élément hôte* générée qui représente le classeur ou la feuille. Pour plus d'informations, consultez [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md).  
  
### Documents Word dans le concepteur  
 Lorsque vous ouvrez le document dans le concepteur, vous pouvez le modifier de la même façon que lorsque vous l'ouvrez directement dans Word. Si vous double\-cliquez sur un mot dans le document, ce mot est sélectionné. Toutefois, si le mot se trouve à l'intérieur d'un contrôle hôte, l'éditeur de code s'ouvre et Visual Studio génère le gestionnaire d'événements par défaut pour le contrôle.  
  
 Le document comporte un fichier de code associé. Le fichier de code contient une classe d'*élément hôte* générée qui représente le document. Pour plus d'informations, consultez [Élément hôte de document](../vsto/document-host-item.md).  
  
### Mode Création et mode Exécution  
 Lorsqu'un document est ouvert dans l'environnement Visual Studio, il l'est toujours en *mode Design*. Certaines tâches, telles que le glissement d'un contrôle hôte vers l'aire du document, ne peuvent être exécutées qu'en mode Design.  
  
 Pour afficher le document en *mode Exécution*, vous devez ouvrir l'application et le document en dehors de Visual Studio. Vous pouvez également générer et exécuter le projet afin d'ouvrir automatiquement le document et l'application en dehors de Visual Studio.  
  
## Éditeur de code  
 L'éditeur de code vous permet d'afficher et de modifier les fichiers de code visibles dans votre solution. Ces fichiers contiennent le code qui définit le comportement de votre solution.  
  
 Pour plus d’informations sur l’éditeur de code, consultez [Écriture de code dans l'éditeur de code et de texte](../ide/writing-code-in-the-code-and-text-editor.md). Pour plus d’informations sur l’écriture de code dans les projets Office, consultez [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md).  
  
## Fenêtre Propriétés  
 La fenêtre **Propriétés** affiche les propriétés des éléments de projet sélectionnés dans l'**Explorateur de solutions** et des éléments d'interface sélectionnés dans le concepteur, tels que les contrôles ou le document dans un projet au niveau du document. Certaines propriétés sont spécifiques à l'application et au document, alors que d'autres sont les mêmes pour tous les projets.  
  
## Fenêtre Sources de données  
 Vous pouvez utiliser la fenêtre **Sources de données** dans les projets Office au niveau du document pour faire glisser une source de données sur votre document et créer un contrôle lié à la source de données. Pour plus d'informations, consultez [Liaison de contrôles à des données dans Visual Studio](../Topic/Binding%20controls%20to%20data%20in%20Visual%20Studio.md).  
  
## Voir aussi  
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Propriétés dans les projets Office](../vsto/properties-in-office-projects.md)  
  
  
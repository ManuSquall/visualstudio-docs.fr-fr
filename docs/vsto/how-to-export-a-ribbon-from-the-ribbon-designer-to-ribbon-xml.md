---
title: "Comment&#160;: exporter un ruban &#224; partir du Concepteur de ruban vers l&#39;&#233;l&#233;ment XML Ribbon | Microsoft Docs"
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
  - "ruban personnalisé, XML"
  - "personnaliser le ruban, XML"
  - "exporter un ruban"
  - "ruban (développement Office dans Visual Studio), exporter"
  - "ruban (développement Office dans Visual Studio), XML"
  - "Concepteur de ruban (développement Office dans Visual Studio)"
  - "XML (développement Office dans Visual Studio), ruban"
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Comment&#160;: exporter un ruban &#224; partir du Concepteur de ruban vers l&#39;&#233;l&#233;ment XML Ribbon
  L'élément **Ruban \(Concepteur visuel\)** ne prend pas en charge tous les types possibles de personnalisations du ruban.  Pour effectuer une personnalisation avancée du ruban, vous pouvez exporter le ruban du concepteur vers l'élément XML Ribbon et modifier directement le XML.  
  
> [!NOTE]  
>  Toutes les valeurs de propriété n'apparaissent pas dans le fichier XML du ruban.  Pour plus d’informations, consultez [Vue d'ensemble du ruban](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Pour exporter un ruban à partir du Concepteur de ruban vers l'élément XML Ribbon  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code du ruban, puis cliquez sur **Concepteur de vues**.  
  
2.  Cliquez avec le bouton droit sur le Concepteur de ruban, puis cliquez sur **Exporter le ruban au format XML**.  
  
     Visual Studio ajoute un fichier XML de ruban et un fichier de code XML de ruban à votre projet.  
  
3.  Dans la classe de code du ruban, recherchez les commentaires commençant par `TODO:.`  
  
4.  Copiez le bloc de code de ces commentaires vers la classe **ThisAddin**, **ThisWorkbook**ou **ThisDocument**, selon le type de solution que vous développez.  
  
     Ce code permet à l'application Microsoft Office de détecter et de charger votre ruban personnalisé.  Pour plus d’informations, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
5.  Dans la classe **ThisAddin**, **ThisWorkbook**ou **ThisDocument**, supprimez les marques de commentaire du bloc de code.  
  
     Une fois que vous avez supprimé les marques de commentaire du code, il doit ressembler à l'exemple suivant.  Dans cet exemple, la classe du ruban est appelée `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  Basculez sur le fichier de code XML du ruban et recherchez la région `Ribbon Callbacks`.  
  
     Elle permet d'écrire des méthodes de rappel pour gérer des actions de l'utilisateur, telles qu'un clic sur un bouton.  
  
7.  Créez une méthode de rappel pour chaque gestionnaire d'événements que vous avez écrit dans le code du Concepteur de ruban.  
  
8.  Déplacez l'ensemble de votre code de gestionnaire d'événements vers les méthodes de rappel et modifiez le code pour utiliser le modèle de programmation d'extensibilité du ruban \(RibbonX\).  
  
     Pour plus d'informations sur l'écriture de méthodes de rappel et l'utilisation du modèle de programmation RibbonX, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
## Voir aussi  
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide d'un élément XML Ribbon](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  
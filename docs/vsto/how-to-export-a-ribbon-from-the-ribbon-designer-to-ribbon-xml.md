---
title: "Comment : exporter un ruban à partir du Concepteur de ruban vers ruban XML | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b73bff8170e351e9e22e95d53ae446895cfdbd2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Comment : exporter un ruban à partir du Concepteur de ruban vers l'élément XML Ribbon
  Le **ruban (Concepteur visuel)** élément ne prend pas en charge tous les types possibles de personnalisations du ruban. Pour personnaliser le ruban de façon avancée, vous pouvez exporter le ruban à partir du concepteur vers ruban XML et modifier directement le XML.  
  
> [!NOTE]  
>  Toutes les valeurs de propriété apparaissent dans le fichier XML du ruban. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Pour exporter un ruban à partir du Concepteur de ruban vers ruban XML  
  
1.  Cliquez sur le fichier de code du ruban dans **l’Explorateur de solutions**, puis cliquez sur **Concepteur de vue**.  
  
2.  Cliquez sur le Concepteur de ruban, puis cliquez sur **exporter un ruban au format XML**.  
  
     Visual Studio ajoute un fichier XML du ruban et un fichier de code XML du ruban à votre projet.  
  
3.  Dans la classe de code du ruban, recherchez les commentaires qui commencent par `TODO:`.  
  
4.  Copiez le bloc de code de ces commentaires à le **ThisAddin**, **ThisWorkbook**, ou **ThisDocument** classe, selon le type de solution que vous développez.  
  
     Ce code permet à l’application Microsoft Office de découvrir et de charger votre ruban personnalisé. Pour plus d'informations, consultez [Ribbon XML](../vsto/ribbon-xml.md).  
  
5.  Dans le **ThisAddin**, **ThisWorkbook**, ou **ThisDocument** de classe, supprimez le bloc de code.  
  
     Une fois que vous les commentaires du code, il doit ressembler à l’exemple suivant. Dans cet exemple, la classe du ruban est appelée `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Basculez vers le fichier de code XML du ruban et de trouver le `Ribbon Callbacks` région.  
  
     Il s’agit où vous écrivez des méthodes de rappel pour gérer les actions utilisateur, comme les clics sur un bouton.  
  
7.  Créez une méthode de rappel pour chaque gestionnaire d’événements que vous avez écrite dans le code du Concepteur de ruban.  
  
8.  Déplacez tout votre code de gestionnaire d’événements à partir des gestionnaires d’événements pour les méthodes de rappel et modifiez le code fonctionne avec le modèle de programmation d’extensibilité du ruban (RibbonX).  
  
     Pour plus d’informations sur l’écriture de méthodes de rappel et l’utilisation du modèle de programmation RibbonX, consultez [ruban XML](../vsto/ribbon-xml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Procédure pas à pas : Création d’un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : création d’un onglet personnalisé à l’aide d’un élément XML Ribbon](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  
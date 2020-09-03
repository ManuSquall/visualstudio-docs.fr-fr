---
title: 'Comment : exporter un ruban à partir du concepteur de ruban vers le ruban XML'
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57918e8a51a3948a2c69eb0c8ab5438b147e44f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543466"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Comment : exporter un ruban à partir du concepteur de ruban vers le ruban XML
  L’élément **Ruban (concepteur visuel)** ne prend pas en charge tous les types possibles de personnalisation du ruban. Pour personnaliser le ruban de manière avancée, vous pouvez exporter le ruban du concepteur vers le ruban XML et modifier directement le code XML.

> [!NOTE]
> Toutes les valeurs de propriété ne s’affichent pas dans le fichier XML du ruban. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Pour exporter un ruban à partir du concepteur de ruban vers le ruban XML

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code du ruban, puis cliquez sur **Concepteur de vues**.

2. Cliquez avec le bouton droit sur le concepteur de ruban, puis cliquez sur **Exporter le ruban vers XML**.

     Visual Studio ajoute un fichier XML de ruban et un fichier de code XML du ruban à votre projet.

3. Dans la classe de code du ruban, localisez les commentaires qui commencent par `TODO:` .

4. Copiez le bloc de code de ces commentaires dans la classe **ThisAddIn**, **ThisWorkbook**ou **ThisDocument** , selon le type de solution que vous développez.

     Ce code permet à l’application Microsoft Office de découvrir et de charger votre ruban personnalisé. Pour plus d'informations, consultez [Ribbon XML](../vsto/ribbon-xml.md).

5. Dans la classe **ThisAddIn**, **ThisWorkbook**ou **ThisDocument** , supprimez les marques de commentaire du bloc de code.

     Une fois que vous avez décommenté le code, celui-ci doit ressembler à l’exemple suivant. Dans cet exemple, la classe Ribbon est appelée `MyRibbon` .

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Basculez vers le fichier de code XML du ruban et recherchez la `Ribbon Callbacks` région.

     C’est là que vous écrivez des méthodes de rappel pour gérer les actions de l’utilisateur, telles que le clic sur un bouton.

7. Créez une méthode de rappel pour chaque gestionnaire d’événements que vous avez écrit dans le code du concepteur de ruban.

8. Déplacez tout votre code de gestionnaire d’événements des gestionnaires d’événements vers les méthodes de rappel et modifiez le code pour qu’il fonctionne avec le modèle de programmation d’extensibilité du ruban (RibbonX).

     Pour plus d’informations sur l’écriture des méthodes de rappel et l’utilisation du modèle de programmation RibbonX, consultez [Ruban XML](../vsto/ribbon-xml.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du ruban XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)

---
title: 'Comment : ajouter des contrôles XMLNode à des documents Word'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd0429374b175da3260c3605f39c90cf2dffb841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544896"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Comment : ajouter des contrôles XMLNode à des documents Word
  **Important** Les informations fournies dans cette rubrique concernant Microsoft Word sont présentées exclusivement pour l’avantage et l’utilisation des personnes et des organisations situées en dehors du États-Unis et de ses territoires, ou qui utilisent ou développent des programmes qui s’exécutent sur les produits Microsoft Word qui étaient sous licence par Microsoft avant le 2010 du 1er janvier, lorsque Microsoft a supprimé une implémentation de fonctionnalités particulières liées au code XML personnalisé de Ces informations relatives à Microsoft Word peuvent ne pas être lues ou utilisées par des personnes ou des organisations du États-Unis ou de ses territoires qui utilisent ou développent des programmes qui s’exécutent sur, les produits Microsoft Word qui étaient sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne se comportent pas de la même façon que les produits sous licence avant cette date ou achetés et sous licence pour une utilisation en dehors du États-Unis.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Quand vous mappez un élément de schéma XML qui n’est pas répétitif à un document Word Microsoft Office, Visual Studio ajoute automatiquement un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle à votre document. Pour plus d’informations sur le mappage d’éléments de schéma XML répétitifs, consultez [Comment : ajouter des contrôles XMLNodes à des documents Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).

> [!NOTE]
> Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle n’est pas disponible à partir de la **boîte à outils** ou de la fenêtre **sources de données** , et il ne peut pas être créé par programmation.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>Pour ajouter un contrôle XMLNode à un document

1. Dans le document dans le concepteur Visual Studio, sur le ruban, cliquez sur l’onglet **développeur** .

    > [!NOTE]
    > Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d’informations, consultez [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. Dans le groupe **XML** , cliquez sur **schéma**.

     La boîte de dialogue **modèles et compléments** s’ouvre.

3. Cliquez sur l’onglet **schéma XML** .

4. Cliquez sur **Ajouter un schéma**.

     La boîte de dialogue **Ajouter un schéma** s’ouvre.

5. Sélectionnez un schéma XML qui contient des éléments de schéma non répétitifs dans la boîte de dialogue **Ajouter un schéma** , puis cliquez sur **ouvrir**.

     La boîte de dialogue **paramètres de schéma** s’affiche.

6. Affectez un alias ou cliquez sur **OK** pour ajouter le schéma sans alias.

     Le schéma est ajouté à la boîte de dialogue **Ajouter un schéma** .

7. Dans la boîte de dialogue **Ajouter un schéma** , cliquez sur **OK**.

8. Le volet Office **structure XML** s’ouvre.

9. Cliquez sur l’élément schéma non répétitif dans le volet Office **structure XML** pour l’ajouter au document.

     Un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle est créé et ajouté au projet.

## <a name="see-also"></a>Voir aussi
- [XMLNode, contrôle](../vsto/xmlnode-control.md)
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

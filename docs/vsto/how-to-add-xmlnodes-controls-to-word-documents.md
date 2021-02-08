---
title: 'Comment : ajouter des contrôles XMLNodes à des documents Word'
description: Découvrez que lorsque vous mappez un élément de schéma XML répétitif à un document Word Microsoft Office, Visual Studio ajoute automatiquement un contrôle XMLNodes à votre document.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c3cbcbe02ee18fafcdff7edbffc376e2502fd175
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836148"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Comment : ajouter des contrôles XMLNodes à des documents Word
  **Important** Les informations fournies dans cette rubrique concernant Microsoft Word sont présentées exclusivement pour l’avantage et l’utilisation des personnes et des organisations situées en dehors du États-Unis et de ses territoires, ou qui utilisent ou développent des programmes qui s’exécutent sur les produits Microsoft Word qui étaient sous licence par Microsoft avant le 2010 du 1er janvier, lorsque Microsoft a supprimé une implémentation de fonctionnalités particulières liées au code XML personnalisé de Ces informations relatives à Microsoft Word peuvent ne pas être lues ou utilisées par des personnes ou des organisations du États-Unis ou de ses territoires qui utilisent ou développent des programmes qui s’exécutent sur, les produits Microsoft Word qui étaient sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne se comportent pas de la même façon que les produits sous licence avant cette date ou achetés et sous licence pour une utilisation en dehors du États-Unis.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Quand vous mappez un élément de schéma XML répétitif à un document Word Microsoft Office, Visual Studio ajoute automatiquement un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle à votre document.

 Pour plus d’informations sur le mappage d’éléments de schéma XML non répétitifs, consultez [Comment : ajouter des contrôles XMLNode à des documents Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

> [!NOTE]
> Le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle n’est pas disponible à partir de la **boîte à outils** ou de la fenêtre **sources de données** , et il n’est pas non plus possible de le créer par programmation.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Pour ajouter un contrôle XMLNodes à un document

1. Dans le document dans le concepteur Visual Studio, sur le ruban, cliquez sur l’onglet **développeur** .

    > [!NOTE]
    > Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d’informations, consultez [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. Dans le groupe **XML** , cliquez sur **schéma**.

     La boîte de dialogue **modèles et compléments** s’ouvre.

3. Cliquez sur l’onglet **schéma XML** .

4. Cliquez sur **Ajouter un schéma**.

     La boîte de dialogue **Ajouter un schéma** s’ouvre.

5. Sélectionnez un schéma XML qui contient des éléments de schéma répétitifs et cliquez sur **ouvrir**.

     La boîte de dialogue **paramètres de schéma** s’affiche.

6. Affectez un alias ou cliquez sur **OK** pour ajouter le schéma sans alias.

     Le schéma est ajouté à la boîte de dialogue **Ajouter un schéma** .

7. Dans la boîte de dialogue **Ajouter un schéma** , cliquez sur **OK**.

     Le volet Office **structure XML** s’ouvre.

8. Cliquez sur l’élément schéma répétitif dans le volet Office **structure XML** pour l’ajouter au document.

     Un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle est créé et ajouté au projet.

## <a name="see-also"></a>Voir aussi
- [XMLNodes, contrôle](../vsto/xmlnodes-control.md)
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
